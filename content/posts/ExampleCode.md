---
title: "Example Code"
date: 2020-09-15T11:30:03+00:00
weight: 21
# aliases: ["/first"]
tags: ["Robotics"]
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

Paste these into main.cpp and platformio.ini respectively:

## main.cpp

![main](/img/main_location.PNG)

```C++
#include <Arduino.h>
#include <Adafruit_BNO055.h>

Adafruit_BNO055 bno = Adafruit_BNO055(55, 0x28, &Wire);

void CalibrateCompass() {
  bno.begin();
  uint8_t system, gyro, accel, mag = 0;
  while (mag < 3) {
    bno.getCalibration(&system, &gyro, &accel, &mag);
    Serial.println("Calibrate your comapass sensor!");
    Serial.print(String(mag) + "/3");
    Serial.println();
    delay(100);
  }
}

double readCompass() {
  sensors_event_t orientationData;
  bno.getEvent(&orientationData, Adafruit_BNO055::VECTOR_EULER);
  return orientationData.orientation.x;
}

void motor1(int power, boolean direction) {
  digitalWrite(2, direction);//DIR 1
  digitalWrite(5, !direction);//DIR 2
  analogWrite(3, power);//POWER
}

void motor2(int power, boolean direction) {
  digitalWrite(8, direction);
  digitalWrite(7, !direction);
  analogWrite(6, power);
}

void motor3(int power, boolean direction) {
  digitalWrite(12, direction);
  digitalWrite(11, !direction);
  analogWrite(4, power);
}

void initializePins() {
  //initialize motor pins
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);
  pinMode(4, OUTPUT);
  pinMode(5, OUTPUT);
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(11, OUTPUT);
  pinMode(12, OUTPUT);

  //initialize ball sensor pins and line sensor pins
  pinMode(14, INPUT);
  pinMode(15, INPUT);
  pinMode(16, INPUT);
  pinMode(17, INPUT);
  pinMode(20, INPUT);
  pinMode(21, INPUT);
  pinMode(22, INPUT);
  pinMode(23, INPUT);
  pinMode(9, INPUT);
  pinMode(10, INPUT);

  //PUT YOUR SETUP CODE HERE!
}


void setup(void)
{
  Serial.begin(115200);
  initializePins();
  CalibrateCompass();

}




void loop(void)
{

  Serial.println("reading sensors ");
  Serial.println("ball sensor 1: " + String(analogRead(14)));
  Serial.println("ball sensor 2: " + String(analogRead(15)));
  Serial.println("ball sensor 3: " + String(analogRead(16)));
  Serial.println("ball sensor 4: " + String(analogRead(17)));
  Serial.println("ball sensor 5: " + String(analogRead(20)));
  Serial.println("ball sensor 6: " + String(analogRead(21)));
  Serial.println("ball sensor 7: " + String(analogRead(22)));
  Serial.println("ball sensor 8: " + String(analogRead(23)));
  Serial.println("push button 1: " + String(digitalRead(9)));
  Serial.println("push button 2: " + String(digitalRead(10)));
  Serial.println("orientation: " + String(readCompass()));
  Serial.println("current runtime: " + String(millis()) + " milliseconds");
  Serial.println("--------------------------------------");


  //first number is power, second is direction
  //ex: motor1(100, 1) spins motor 1 at 100/255 speed in one direction
  //ex: motor1(255, 0) spins motor 1 at 255/255 (100%) speed in the other direction
  motor1(100, 1);
  motor2(50, 0);
  motor3(255, 1);
  delay(1000); // freeze program for 1 second

  //stop by writing 0 power to all motors (direction doesnt matter)
  motor1(0, 1);
  motor2(0, 0);
  motor3(0, 1);
  delay(1000); // freeze program for 1 second




}

```


## platformio.ini

![platformio.ini](/img/platformioini_location.PNG)

```C++
; PlatformIO Project Configuration File
;
;   Build options: build flags, source filter
;   Upload options: custom upload port, speed and extra flags
;   Library options: dependencies, extra library storages
;   Advanced options: extra scripting
;
; Please visit documentation for the other options and examples
; https://docs.platformio.org/page/projectconf.html

[env:teensy41]
platform = teensy
board = teensy41
framework = arduino
monitor_speed = 9600
lib_deps = adafruit/Adafruit BNO055@^1.6.1
            SPI

```
