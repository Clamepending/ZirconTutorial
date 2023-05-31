---
title: "STEP 100"
date: 2020-09-15T11:30:03+00:00
weight: 100
# aliases: ["/first"]
tags: ["hardware"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Print if ball"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
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

We will now react to the ball!


PUT VIDEO OF PRINTING WHEN BALL IS IN FRONT AND ANOTHE PRINT WHEN IT IS NOT
{{< youtube id="" >}}


HINT:

We need to get the ball sensor value using 
```C++
analogRead(A8)
```
and check if the value indicates there is a ball in front with in if statement.

for example
```C++
if (analogRead(A8) < 500) {
    // CODE HERE WHEN ROBOT SEES THE BALL
} else {
    // CODE HERE WHEN ROBOT DOES NOT SEE THE BALL
}
```
checks if there is a ball in front because analogRead(A8) returns around 1024 when the ball sensor does NOT see the ball, and a lower number when it does.


500 is an arbitrary number, you may have to adjust it if the robot is not responsing or responding all the time.

## Problem

Make the robot go forwards if the ball is in front, otherwise rotate.

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

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

}

void loop(void)
{
    if (analogRead(A8) < 500) {
        motor1(0, 0); // stop motor 1
        motor2(100, 0); // make motor 2 go at 100% speed in direction 0
        motor3(100, 0); // make motor 3 go at 100% speed in direction 0
    } else {
        motor1(100, 0); // stop motor 1
        motor2(100, 0); // make motor 2 go at 100% speed in direction 0
        motor3(100, 1); // make motor 3 go at 100% speed in direction 0
    }

  

}
```

{{< /collapse >}}

