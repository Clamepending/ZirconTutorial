---
title: "If statements"
date: 2020-09-15T11:30:03+00:00
weight: 16
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

{{< youtube id="" >}}

## Problem

find the prime factors of 1294892647

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    //the strategy here is to start at 2 and see if any 
    //number divides 1294892647 with remainder 0
    //if not, try a higher number until you can
    //then print that out and divide that factor out of 
    //1294892647 and restart the process until you get 1

    int number = 1294892647;

    //start by trying to divide by 2 because everything 
    //is divisible by 1

    int testFactor = 2;

    Serial.println("Factors are: ");

    //while there are factors left
    while (number > 1){

        //if testFactor is a factor of number
        if(number % testFactor == 0){
            //divide out testFactor from number
            number = number/testFactor;

            //print out the factor that was found
            Serial.println(String(testFactor));

            //reset the testFactor
            testFactor = 1;
        }

        //increase the test factor by 1
        testFactor = testFactor + 1;
      
    }

    //make the output readable by slowing it down
    delay(1000);
}

/**
 * Factors are: 
59
2411
9103
**/
    
```

{{< /collapse >}}

