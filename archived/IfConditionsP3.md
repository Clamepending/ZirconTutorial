---
title: "If statements"
date: 2020-09-15T11:30:03+00:00
weight: 16.2
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

fill in the condition (REPLACE THIS) in the if statement to print out all the numbers from 0 to 5 and 15 to 99 (include 0, 5, and 15).

DONT modify the for loop.

HINT:

```C++
||
```
is an OR statement.
It returns true if either conditions are true.

```C++
true || true // returns true
```
```C++
true || false // returns true
```
```C++
false || true // returns true
```
```C++
false || false // returns false
```

using it in an if statment to see if x is 3 or 4 looks like this:

```C++
if (x == 3 || x == 4) {
    // code to execute when x is 3 or x is 4
} 
```



```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    for (int i = 0; i < 100; i = i + 1) {
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
    for (int i = 0; i < 100; i = i + 1) {
        if (i < 6 || i > 14) {
        Serial.println(String(i));
        } 
    }
    
    
    

    //make the output readable by slowing it down
    delay(1000);
}

```
there are other ways to do this, such as using >= like this
```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    for (int i = 0; i < 100; i = i + 1) {
        if (i <= 5 || i >= 15) {
        Serial.println(String(i));
        } 
    }
    
    
    

    //make the output readable by slowing it down
    delay(1000);
}

```


{{< /collapse >}}

