---
title: "Example Code"
date: 2020-09-15T11:30:03+00:00
weight: 9999
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
#include <zirconLib.h>


void setup(void)
{
  Serial.begin(115200);
  InitializeZircon();

}


void loop(void)
{

  Serial.println("reading sensors ");
  Serial.println("ball sensor 1: " + String(readBall(1)));
  Serial.println("ball sensor 2: " + String(readBall(2)));
  Serial.println("ball sensor 3: " + String(readBall(3)));
  Serial.println("ball sensor 4: " + String(readBall(4)));
  Serial.println("ball sensor 5: " + String(readBall(5)));
  Serial.println("ball sensor 6: " + String(readBall(6)));
  Serial.println("ball sensor 7: " + String(readBall(7)));
  Serial.println("ball sensor 8: " + String(readBall(8)));
  Serial.println("push button 1: " + String(readButton(1)));
  Serial.println("push button 2: " + String(readButton(2)));
  Serial.println("orientation: " + String(readCompass()));
  Serial.println("current runtime: " + String(millis()) + " milliseconds");
  Serial.println("--------------------------------------");

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
lib_deps = clamepending/ZirconLib@^1.0.17


```
