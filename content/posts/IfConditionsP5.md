---
title: "If statements"
date: 2020-09-15T11:30:03+00:00
weight: 16.4
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

print out all the numbers divisible by 3 from 0 to 21 (include 0 and 21) using an if statement.

Divisible means dividing 21 by it results in no remainder. 

example:

21 is divisible by 3 because 21/3 = 7

22 is not divisible by 3 because 22/3 = 7 with remainder 1

output should look like:

0

3

6

9

...

18

21

HINT:

the % operation will be useful. % returns the remainder:
```C++
22 % 3 //returns 1
```
```C++
31 % 7 //returns 3
```
```C++
9 % 3 // returns 0
```

HINT 2:
this program should be VERY similar to the previous one.


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
        if (i % 3 == 0) {
        Serial.println(String(i));
        } 
    }
    
    
    

    //make the output readable by slowing it down
    delay(1000);
}

```


{{< /collapse >}}

