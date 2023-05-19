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
platformio.ini is the configuration file for the project. ou can find it in the file finder on the left side
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

Dont worry about the code at the top. The println() commands in the void loop(void) should look familiar.

This code prints out the sensor values for most of the sensors on the Zircon

Each sensor (such as a button) is connected to a pin on the Teensy (the main microcontroller in the picture below). 

![teensy](/img/teensy.PNG)


There are analog and digital sensors. We will talk about digital sensors later. 

Analog sensors normaly have an output pin that has a varying voltge depending on the state of the sensor. 

For example, the output pin might be 3.3V when button is pressed, and 0V when the button is not pressed. 
So we "read" sensors by reading the voltage of the sensor pin.

The command to do this in C++ is
```C++
analogRead(pin_number);
```

To read pin A5 for example, we would write
```C++
analogRead(A5);
```

Just reading the pin doesnt do much, so we can store the value in a variable like this:
```C++
int sensorData = analogRead(A5);
```
Now we can do calcualtions with sensorData as you learned in the previous C++ section.

to print the data to the computer, we write
```C++
Serial.println(String(sensorData));
```

Try uploading and monitoring the program you pasted in above. You should get readings for the sensors on the Zircon. 

Try turning the ball on and moving it close to the robot to see how the values change.

Also try pushing the buttons to see how the data from the button changes from a 0 to a 1 when pressed.

## Problem

This is an example that reads the value of sensor on pin 9 (a push button) and prints it in the serial monitor on your computer every second.

(you can ignore things outside void loop())

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
}


void setup(void)
{
  Serial.begin(115200); // WE NEED THIS TO PRINT THINGS TO THE COMPUTER
  initializePins();

  //PUT YOUR SETUP CODE HERE!


}

void loop() {

    int sensorData = analogRead(9);

    Serial.println(String(sensorData));    
    
    delay(1000);
}
```

Copy-paste and upload this to see if it works. Make sure you click the monitor button after you upload to see the serial monitor.

Pushing the button labeled pin 9 should change the number being printed.

Modify the program to print out the sensor data of the right pushbutton (connected to pin 10 instead of 9).

You should see the numbers react in real time when you press the button.

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
}


void setup(void)
{
  Serial.begin(115200); // WE NEED THIS TO PRINT THINGS TO THE COMPUTER
  initializePins();

  //PUT YOUR SETUP CODE HERE!


}

void loop() {

    int sensorData = analogRead(10);// THIS IS THE ONLY LINE THAT CHANGED

    Serial.println(String(sensorData));    
    
    delay(1000);
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

