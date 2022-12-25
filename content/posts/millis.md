---
title: "millis()"
date: 2020-09-15T11:30:03+00:00
weight: 17
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 16"
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

measure how long it took to compute the factors of 1294892647 (your previous program)

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {
    
    Serial.begin(9600);

}   

void loop() {
    
    //store the time at the start
    int start = millis();

    //below is the program from before:

    int number = 1294892647;
    int testFactor = 2;

    Serial.println("Factors are: ");
    while (number > 1){
      if(number % testFactor == 0){
        number = number/testFactor;
        Serial.println(String(testFactor));
        testFactor = 1;
      }
      testFactor = testFactor + 1;
      
    }


    //Print the difference between current time and start
    Serial.println("the factorization took: " + 
    String(millis() - start) + 
    " milliseconds");

    delay(1000);
}

/**
 * Factors are: 
59
2411
9103
the factorization took: 18 milliseconds
**/
    
```

{{< /collapse >}}

