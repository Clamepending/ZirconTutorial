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
  while (mag < 3 || gyro < 3) {
    bno.getCalibration(&system, &gyro, &accel, &mag);
    Serial.println("Calibrate your comapass sensor!");
    Serial.println();
    Serial.print(" Gyro=");
    Serial.print(gyro);
    Serial.print(" Mag=");
    Serial.println(mag);
    delay(100);
  }
}

double readCompass() {
  sensors_event_t orientationData;
  bno.getEvent(&orientationData, Adafruit_BNO055::VECTOR_EULER);
  return orientationData.orientation.x;
}


void setup(void)
{
  Serial.begin(115200);

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


  CalibrateCompass();
  
}




void loop(void)
{


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

  //Its important to have a delay if you are just printing because your computer Terminal will lag (be slow) if you print without a delay
  //but if you are not printing things, removing the delay will make your robot react quicker
  delay(100);
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
