---
title: "If statements"
date: 2020-09-15T11:30:03+00:00
weight: 16.3
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 15"
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



## Problem

fill in the condition (REPLACE THIS) in the if statement to print out all the even numbers from 0 to 21 (include 0).

if we have a variable
```C++
int a = 5;
```

```C++
a % 2 == 0 //returns false
```
Checks if a is even.

```C++
a % 2 == 1 //returns true
```


DONT modify the for loop.


```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    for (int i = 0; i < 21; i = i + 1) {
        if (REPLACE THIS) {
        Serial.println(String(i));
        } 
    }
    
    
    

    //make the output readable by slowing it down
    delay(1000);
}

```


## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    for (int i = 0; i < 21; i = i + 1) {
        if (i % 2 == 0) {
        Serial.println(String(i));
        } 
    }
    
    
    

    //make the output readable by slowing it down
    delay(1000);
}

```


{{< /collapse >}}

