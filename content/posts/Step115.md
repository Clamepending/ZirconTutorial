---
title: "STEP 115"
date: 2020-09-15T11:30:03+00:00
weight: 115
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Operations and Data Types"
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

{{< youtube id="cfNkhwL1bmw" >}}

## Problem

Compute (1 + 1), then print out "the answer is: (your computed answer)" from the teensy every second

So if the answer is 21, you should print "the answer is: 21" to the computer every second

![2](/img/2.png)

HINT:

to combine a String and an Integer, we first need to convert the Integer to a String.

Use String() to do that:
```C++
String(3) returns "3"

"hello " + String(3) returns "hello 3"

Serial.println("hello " + String(5 + 4)); prints "hello 9" to the computer

```

```C++
int a = 0;
a = 6 + 9
Serial.println("hello " + String(a));
```
prints "hello 15" to the computer

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {

    Serial.begin(9600);

}   

void loop() {

    // we use a double because it can handle 
    //very big numbers, floats, and very small numbers.
    int answer = 1 + 1; 
    
    //we use String() to convert answer from a double 
    //to a float to combine it with a string to print it out
    Serial.println("the answer is: " + String(answer));
    
    
    delay(1000);
}
```

{{< /collapse >}}

