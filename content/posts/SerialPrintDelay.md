---
title: "Serial, Printing, Delay"
date: 2020-09-15T11:30:03+00:00
weight: 13
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 9"
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

{{< youtube id="xTUMSJTGjw0" >}}




## void setup(void)

The code inside setup(void) runs once at the start

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

## Problem

print "YO" to the serial port every 0.5 seconds (500 milliseconds) forever (until you press Ctrl + C to quit monitor)

![YO](/img/.png)


## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>
 
void setup() {
    // put your setup code here, to run once:
 
    Serial.begin(9600);
 
}   s
 
void loop() {
    // put your main code here, to run repeatedly
 
    Serial.println("YO");
    
    delay(500);
}
```

{{< /collapse >}}



