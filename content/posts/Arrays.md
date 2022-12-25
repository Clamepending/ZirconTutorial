---
title: "Arrays"
date: 2020-09-15T11:30:03+00:00
weight: 19
# aliases: ["/first"]
tags: ["software"]
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

{{< youtube id="" >}}

## Problem

Use an arrary to find the sum of {230, 345, 45, 1, 45, 95, 5325, 53, 23, 5, 46, 7, 8, 5, 6, 5, 46, 6}

## Solution


{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   


void loop() {

    //define a list and paste in the values
    int listToSum[] = {230, 345, 45, 1, 45, 95, 5325, 53, 23, 
5, 46, 7, 8, 5, 6, 5, 46, 6};


    //initialize a counter to keep track of the total
    int total = 0;

    //sizeof(listToSum) returns the size in bytes
    //each int is 4 bytes so we have to divide
    //sizeof(listToSum) by sizeof(int) to get
    //the length of the list
    int sizeOFListToSum = sizeof(listToSum)/sizeof(int);

    //go through all numbers in listToSum
    for(int i = 0; i < sizeOFListToSum; i++){

      //add each number to total
      total = total + listToSum[i];

    }

    //print the total
    Serial.println("total: " + String(total));

    //make output easier to read
    delay(1000);

}



/**The answer is 6296
 * Output:
total: 6296
total: 6296
**/
```

{{< /collapse >}}
