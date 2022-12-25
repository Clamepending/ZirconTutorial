---
title: "Variables, Comments, Loops"
date: 2020-09-15T11:30:03+00:00
weight: 15
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 14"
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

{{< youtube id="" >}}

## Problem

The fibonacci sequence is 1, 1, 2, 3, 5, 8, 13, 21, ...

the next element is found by adding the two numbers before it

Compute the 40th fibonacci number

this one is hard!

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

    void setup() {
        // put your setup code here, to run once:
    
        Serial.begin(9600);
    
    }   
    
    void loop() {
        //we define a and b to be 
        //the last 2 numbers we have so far
        int a = 1;
        int b = 1;
    
    
        //we can declare a variable without assigning it to 
        //a specific value like 0. 
        //we are essentially promissing to assign a value to 
        //it before we use it
        //the code would work the same if you just said 
        //int nextNumber = 0;
        int nextNumber; 
    
        //we set i < 38 because we set the first two fibinacci 
        //numbers 1, 1 as default, so at i = 0, 
        //we are calculating the 3rd fibinacci number
        //so 40 - 2 = 38
        for(int i = 0; i < 38; i++){
            //here we compute the next number
            //if this is the first run, it is the 
            //first time nextNumber is assigned
            nextNumber = a + b;
            a = b;
            b = nextNumber;
        }
        Serial.println(nextNumber);
        
        delay(700);
    }
//answer is 102334155

{{< /collapse >}}

