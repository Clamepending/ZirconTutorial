---
title: "Demo Program"
date: 2024-04-15T11:30:03+00:00
weight: null
# aliases: ["/first"]
tags: []
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: ""
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: false
hideSummary: false
searchHidden: true
# ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
# editPost:
#     URL: "https://github.com/<path_to_repo>/content"
#     Text: "Suggest Changes" # edit text
#     appendFilePath: true # to append file path to Edit link
---


```c++
#include <Arduino.h>
#include <zirconLib.h>

#define LINE_THRESHOLD 650
#define MOTOR_POWER 140
#define BALL_CALIBRATION_X 0
#define BALL_CALIBRATION_Y 0

// utils
struct Vector2D {
    float x;
    float y;

    // Default constructor
    Vector2D() : x(0), y(0) {}

    // Parameterized constructor
    Vector2D(float x, float y) : x(x), y(y) {}

    // Method to convert the vector to a string
    String toString() const {
        return "(" + String(x) + ", " + String(y) + ")";
    }

    // Method to print the vector
    void print() const {
        Serial.println(toString());
    }
};

// Directions for sensors arranged clockwise from front
const float angles[8] = {
    M_PI / 2, M_PI / 4, 0, -M_PI / 4,
    -M_PI / 2, -3 * M_PI / 4, -M_PI, 3 * M_PI / 4
};

// Function to read ball sensors and compute the resulting direction vector
Vector2D readBallSensors() {
    float sensorValues[8];

    // Read sensor values
    for (int i = 0; i < 8; i++) {
        sensorValues[i] = readBall(i + 1); // Assuming readBall takes sensor ID 1 to 8
    }

    Vector2D result;

    // Sum the directions weighted by sensor values
    for (int i = 0; i < 8; i++) {
        result.x += sensorValues[i] * cos(angles[i]);
        result.y += sensorValues[i] * sin(angles[i]);
    }

    return result;
}

void moveMotors(const Vector2D& direction, float rotationFactor) {
    float angle = atan2(direction.y, direction.x);
    // Serial.println("angle " + String(180*angle/M_PI));
    

    // Calculate motor powers (assuming 3 omni-directional wheels)
    float motor1Power = MOTOR_POWER*max(min(sin(angle - 5*M_PI/6) + rotationFactor, 1), -1);
    float motor2Power = MOTOR_POWER*max(min(sin(angle - 1*M_PI/6) + rotationFactor, 1), -1);
    float motor3Power = MOTOR_POWER*max(min(sin(angle - 9*M_PI/6) + rotationFactor, 1), -1);

    // Convert the powers to suitable PWM values and set motor directions
    motor1(abs(motor1Power), motor1Power < 0 ? 1 : 0);
    motor2(abs(motor2Power), motor2Power < 0 ? 1 : 0);
    motor3(abs(motor3Power), motor3Power < 0 ? 1 : 0);


}





int goalAngle = 0;


void setup(void)
{
  Serial.begin(115200);
  InitializeZircon();
  motor1(50, 0);
  delay(500);
  motor1(0,0);
  while (readButton(1) == 0) {
    goalAngle = readCompass();
  }
}

float move_angle_from_default;
Vector2D moveVector = Vector2D(0, 0);
Vector2D ballVector;

void loop(void)
{

  // read ball sensors
  ballVector = readBallSensors();
  Serial.println("ball vector: " + ballVector.toString());

  // adjust ball detection for calibration
  ballVector.x += BALL_CALIBRATION_X;
  ballVector.y += BALL_CALIBRATION_Y;



  int compassDiff = readCompass() - goalAngle;
  if (compassDiff > 180) {
    compassDiff -= 360;
  } else if (compassDiff < -180) {
    compassDiff += 360;
  }

  Serial.println("ball vector: " + ballVector.toString() 
    + " line sensor 1: " + String(readLine(1)) 
    + " line sensor 2: " + String(readLine(2)) 
    + " line sensor 3: " + String(readLine(3)) 
    );


  if (readLine(1) > LINE_THRESHOLD) {
    motor1(MOTOR_POWER, 0);
    motor2(MOTOR_POWER, 1);
    motor3(0, 0);
  } else if (readLine(2) > LINE_THRESHOLD) {
    motor1(0, 0);
    motor2(MOTOR_POWER, 0);
    motor3(MOTOR_POWER, 1);
  } else if (readLine(3) > LINE_THRESHOLD) {
    motor1(MOTOR_POWER, 1);
    motor2(0, 0);
    motor3(MOTOR_POWER, 0);





    
  } else {
    

    // orbit
    
    float angle = atan2(ballVector.y, ballVector.x);
    if (angle > M_PI) {
      angle -= M_PI;
    } else if (angle < -M_PI) {
      angle += M_PI;
    }
    float angle_from_front = angle - M_PI/2;
    float orbit_addition = min(M_PI/2, M_PI*(0.04f * pow(M_E, 0.12f * abs(180*angle_from_front/M_PI)))/180);
    
    float ball_vec_magnitude = sqrt(ballVector.x * ballVector.x + ballVector.y * ballVector.y);
    float dampened_orbit_addition = orbit_addition * max(1.0, 0.04f * pow(M_E, 0.002f * (ball_vec_magnitude - 100)));
    
    if (angle_from_front < 0) {
      dampened_orbit_addition *= -1;
    } 

    move_angle_from_default = angle_from_front + dampened_orbit_addition + M_PI/2;
    
    moveVector.x = 0.01 * cos(move_angle_from_default) + 0.9 * moveVector.x;
    moveVector.y = 0.01 * sin(move_angle_from_default) + 0.99 * moveVector.x;


    if (ball_vec_magnitude < 300) {
      motor1(0,0);
      motor2(0,0);
      motor3(0,0);
    } else {
      moveMotors(moveVector, compassDiff/180.0);
    }
    
  }




}
```