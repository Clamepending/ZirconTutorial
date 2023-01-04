---
title: "Robotics"
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
anlogWrite();
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




Thecommand to do this in C++ is
```C++
analogRead();
```

To read pin A5 for example, we would write
```C++
analogRead(A5);
```

Just reading the pin doesnt do much, so we can store the valuein a variable like this:
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