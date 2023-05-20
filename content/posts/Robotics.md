---
title: "Robotics"
date: 2020-09-15T11:30:03+00:00
weight: 20
# aliases: ["/first"]
tags: ["robotics"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 19"
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

Now we can combine C++ and Zircon to make a soccer robot.

We will use C++ to read sensor data and actuate motors. 


Copy and paste this into your main.cpp file:

![main](/img/mainnavigation.png)

```C++
#include <Arduino.h>
#include <zirconLib.h>


void setup(void)
{
  Serial.begin(9600);
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
platformio.ini is the configuration file for the project. You can find it in the file finder on the left side
If you get any library errors or board version errors, this is the place to look.

![platformio.ini](/img/filenavigation.png)

paste the following code into platformio.ini

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
monitor_speed = 115200
lib_deps = adafruit/Adafruit BNO055@^1.6.1
            SPI

```

Dont worry if you dont understand the code yet, we will explain it below. The println() commands in the void loop(void) should look familiar.

This code prints out the sensor values for most of the sensors on the Zircon.


Try uploading and monitoring the program you pasted in above. You should get readings for the sensors on the Zircon. 

Try turning the ball on and moving it close to the robot to see how the values change.

Also try pushing the buttons to see how the data from the button changes from a 0 to a 1 when pressed.


### Explanation

Each sensor (such as a button) is connected to a pin on the Teensy (the main microcontroller in the picture below). 

![teensy](/img/teensy.PNG)


There are analog and digital sensors. We will talk about digital sensors later. 

Analog sensors display a range of values depending on the state of the sensor. 

For example, the output pin might be 1024 when an infrared sensor sees infrared, 0 when the sensor does not, and 567 when the sensor sees a little bit of infrared. 

So we "read" sensors by calling the corresponding function.

Lets say we want to read how much the front ball sensor sees the ball.

Since the ball emits infrared, we have infrared sensors all round the robot. The one in front is the 1st one so to read it we can say:


```C++
readBall(1);
```
This calls the function readBall() and lets it know you want to read the 1st sensor (the one pointing forwards). The robot then reads the 1st ball sensor and gets an integer (the sensor reading).

For example, if readBall(1) returned 100, then we can imagine the program replacing th readBall command with the number 100.

so code like this
```C++
Serial.println("value of ball sensor 1: " + String(readBall(1)));
```
turns into code like this
```C++
Serial.println("value of ball sensor 1: " + String(100));
```

And the program goes on. 


There are 8 ball sensors on the kit so we can pass in the numbers 1 - 8 to read each of the sensors:

```C++
readBall(1); //reads first infrared sensor
readBall(2); //reads second infrared sensor
readBall(3); //reads third infrared sensor
readBall(4); //reads fourth infrared sensor
readBall(5); //reads fifth infrared sensor
readBall(6); //reads sixth infrared sensor
readBall(7); //reads seventh infrared sensor
readBall(8); //reads eighth infrared sensor
```

To print what we read to the computer, we can do:

```C++
Serial.println("value of ball sensor 1: " + String(readBall(1)));
```

Which is most of what the code you copy-pasted above does.

we can also achieve the same result by storing the value in a variable because the value is an int:

```C++
int x = readBall(1); //stores what we measured into x
```

Printing x would print the value that we saved:

```C++
int x = readBall(1); //stores what we measured into x

Serial.println("value of ball sensor 1: " + String(x));
```



Now we can do calculations with real time data from sensors with the skills you learned in the previous C++ section!

For example we can write if statements with sensor readings like this:

```C++
if (readBall(1) > 500) {
  Serial.println("I see the ball");
} else {
  Serial.println("I dont see the ball");
}
```

or like this (same thing) using a variable x:

```C++
int x = readBall(1);
if (x > 500) {
  Serial.println("I see the ball");
} else {
  Serial.println("I dont see the ball");
}
```



## Problem

Change the code you pasted above to only print the reading of pushbutton 2.

i.e print

push button 2: (reading of button 2)

to your computer where (reading of button 2) is replaced with realtime readings of button 2. Check by pressing button 2 to see if the value changes.

Hint:
Make sure you are pressing button 2 not button 1. 


Hint:
Make sure you are reading from button 2 not button 1.


Hint:
Make sure you surround your sensor reading function with String() to convert the int value returned to a String. (wierd things happen if you try combining numbers and Strings in C++ if you dont convert numbers to Strings first)

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>
#include <zirconLib.h>


void setup(void)
{
  Serial.begin(9600);
  InitializeZircon();

}


void loop(void)
{

  // Serial.println("reading sensors ");
  // Serial.println("ball sensor 1: " + String(readBall(1)));
  // Serial.println("ball sensor 2: " + String(readBall(2)));
  // Serial.println("ball sensor 3: " + String(readBall(3)));
  // Serial.println("ball sensor 4: " + String(readBall(4)));
  // Serial.println("ball sensor 5: " + String(readBall(5)));
  // Serial.println("ball sensor 6: " + String(readBall(6)));
  // Serial.println("ball sensor 7: " + String(readBall(7)));
  // Serial.println("ball sensor 8: " + String(readBall(8)));
  // Serial.println("push button 1: " + String(readButton(1)));
  Serial.println("push button 2: " + String(readButton(2)));
  // Serial.println("orientation: " + String(readCompass()));
  // Serial.println("current runtime: " + String(millis()) + " milliseconds");
  // Serial.println("--------------------------------------");

}

```

{{< /collapse >}}

## Initialization

FEEL FREE TO SKIP THIS PART if you like.

This step is easy to forget but is very important. 

This is mostly taken care of for you in the 
```C++
initializePins(); 
```
function we call in void setup(void)

Below is the explanation for the inner workings of initializePins(); 

This is the definition of the initializePins() function you pasted towards the top of your program.
```C++
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
}
```

Any pin that is used (connected to a sensor for example) needs to be initialized. 

It is just how microcontrollers work. So before you start doing analogRead(), you need to call pinMode(); on each pin you use to be run once at the start.

If we wanted to setup pin A5, we would write
```C++
pinMode(A5, INPUT); //all caps INPUT
```
This initalizes pin A5 as an input pin and allows the microncontroller to analogRead(A5); in your program.

Serial.println(); also has an initialization that looks like 
```C++
Serial.begin(9600);
```

So put that during the setup to use Serial.println() in your program.

