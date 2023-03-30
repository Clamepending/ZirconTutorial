---
title: "Movement"
date: 2020-09-15T11:30:03+00:00
weight: 21
# aliases: ["/first"]
tags: ["robotics"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 20"
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

Recap:

we can put in values from 0 - 255 in the power argument, and 0 or 1 in the direction argument.

for example:
```C++
motor1(100, 0);
```
would make motor 1 spin in direction 0 at 100/255 power (39%)

```C++
motor2(255, 1);
```
would make motor 2 spin in direction 1 (the other direction) at 255/255 power (100%)


![motor labels](/img/motorlabels.png)
The arrows indicate which way the motor spins when direction is set to 0.

## Problem

### remember to PUT YOUR ROBOT ON SOMETHING ROUND (like a roll of tape) so the motors are FLOATING

Change the program to make the robot rotate clockwise at full speed (255/255).



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

  motor1(255, 0); // make motor 1 go at 100% speed in direction 0
  motor2(255, 0); // make motor 2 go at 100% speed in direction 0
  motor3(255, 1); // make motor 3 go at 100% speed in direction 1

}
```

{{< /collapse >}}
