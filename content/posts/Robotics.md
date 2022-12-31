---
title: "Robotics"
date: 2020-09-15T11:30:03+00:00
weight: 19
# aliases: ["/first"]
tags: ["robotics"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 18"
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

Each sensor (such as a button) is connected to a pin on the Teensy (the main microcontroller). There are analog and digital sensors. We will talk about digital sensors later. Analog sensors normaly have an output pin that has a varying voltge depending on the state of the sensor. For example, the output pin might be 3.3V when button is pressed, and 0V when the button is not pressed. 
So we "read" sensors by reading the voltage of the sensor pin.

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