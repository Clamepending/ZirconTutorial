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

We will move the motors!

Copy and paste this example program into your main.cpp file.

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
Do not worry about the functions like initializePins() at the top.

The only thing we need to focus on is the 

```C++
void setup(void)
{

}
```

and the

```C++
void loop(void)
{

}
```

## void setup(void)

The commands inside 
```C++
void setup(void)
{

}
```
run once when the robot powers on. It is used to start or initialize sensors. Put code here if you want to do something at the very start of the program.

## void loop(void)

The commands inside 
```C++
void loop(void)
{

}
```
run forever over and over again after setup(void). This is the main part of the program. Put code here if you want to do something over and over again (most code goes here) such as always looking for a ball.

## Motors

To make things simple, we have defined the functions
```C++
motor1(power, direction);
motor2(power, direction);
motor3(power, direction);
```

we can put in values from 0 - 255 in the power argument, and 0 or 1 in the direction argument.

for example:
```C++
motor1(100, 0);
```
would make motor 1 spin in direction 0 at 50/255 power (39%)

```C++
motor2(255, 1);
```
would make motor 2 spin in direction 1 (the other direction) at 255/255 power (100%)


Now try uploading and running the program. The robot should move and then stop.

Try changing the commands to make the robot go forwards.


# Motor Control in-depth

## This part is not essential, and can be ignored. It goes into detail of motor control beyond Zircon

The following is talking about the inner wokrings of the functions motor1(), motor2(), mototr3():

```C++
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
```


Instead of having the microcontroller directly connected to the motors, there is a device called the motor driver that takes care of many things such as switching direction, high power switching, and noise protection.

To communicate to the motor driver what we wnt it to do, we have 3 pins for each motor. 
2 of them are direction pins, and 1 is a power pin.

## direction pins

The direction pins communicate the direction. if we write a logic HIGH (3.3 volts or analogWrite(255)) to one pin and write a logic LOW (0 volts or analogWrite(0)) to the other pin, the motor will spin in one direction.

Swapping the HIGH and LOW pin reverses the direction. If both direction pins are HiGH, or if both are LOW, the motor driver will apply a braking force (motor will just stop).

## power pin

How do we control the speed of the motor?
The power pin.

The PWM duty cycle of the power pin controls the speed.

What is PWM and PWM duty cycle?

{{< youtube id="ISzRh5eN_Pg" >}}

{{< youtube id="YmPziPfaByw" >}}

{{< youtube id="4PtepH8CcEE" >}}

Don't worry if you didnt understand everything. Feel free to search things on google and youtube when you dont understand.

Writing a 100% duty cycle to the power pin translates to a 100% power of the motor.
Writing a 25% duty cycle to the power pin translates to a 25% power of the motor.

The commmnd to write a PWM signal to a pin is 
```C++
analogWrite();
```

Writing a 0% duty cycle to pin 3 would look like:
```C++
analogWrite(3, 0);
```

The first argument is th epin number and the second is the duty cycle amount.

Instead of 100 being 100%, 255 is the maximum because to computers that work in binary, 256 is a nicer number than 101 (we include 0 as a number).
So writing 100% duty cycle to pin 5 would look like:
```C++
analogWrite(3, 255);
```

## Motor control pins

Here are the direction and power pins associated with each motor:




The command to do this in C++ is
```C++
analogRead();
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
Serialprintln(String(sensorData));
```

## Initialization

This step is easy to forget but is very important. Any pin that is used needs to be initialized. It is just how microcontrollers work. So before you start doing analogRead(), you need to put pinMode(); in the setup part of your program to be run once at the start.

If we wanted to setup pin A5, we would write
```C++
pinMode(A5, INPUT);//all caps INPUT
```
This initalizes pin A5 as an input pin and allows the microncontroller to analogRead(A5); in your program.

Serial.println(); also has an initialization that looks like 
```C++
Serial.begin(9600);
```

So put that during the setup to use Serial.println() in your program.


## Example

This is an example that reads the value of sensor on pin A9 (a push button) and prints it in the serial monitor on your computer every second.

```C++
#include <Arduino.h>

void setup() {

    Serial.begin(9600);

    pinMode(A9, INPUT);

}   

void loop() {

    int sensorData = analogRead(A9);

    Serial.println(String(sensorData));    
    
    delay(1000);
}
```

Copy-paste and upload this to see if it works. Make sure you click the monitor button after you upload to see the serial monitor.

Pushing the left button should change the number being printed.

## Problem

Modify the above program to print out the sensor data of the right pushbutton (connected to pin A10).

You should see the numbers react in real time when you press the button.

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {

    Serial.begin(9600);

    pinMode(A10, INPUT);

}   

void loop() {

    int sensorData = analogRead(A10);

    Serial.println(String(sensorData));    
    
    delay(1000);
}
```

{{< /collapse >}}