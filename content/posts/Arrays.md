---
title: "Arrays"
date: 2020-09-15T11:30:03+00:00
weight: 
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true
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

Use an arrary to find the sum of {230, 99, 45, 1, 45}

HINT:
we can declare an array as
```C++
int listToSum[] = {230, 99, 45, 1, 45};
```
and iterate through the elements with a for loop

Lists are indexed starting from 0, so the first element is the 0th element.

To get the 1st element of listToSum we do
```C++
listToSum[0] // returns 230
```

To get the 5th element of listToSum we do
```C++
listToSum[4] // returns 45
```

To get the ith element (useful in a for loop) of listToSum we do
```C++
listToSum[i]
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

    //define a list and paste in the values
    int listToSum[] = {230, 99, 45, 1, 45};


    //initialize a counter to keep track of the total
    int total = 0;

    //go through all numbers in listToSum
    for(int i = 0; i < 5; i++){
      //add each number to total
      total = total + listToSum[i];

    }

    //print the total
    Serial.println("total: " + String(total));

    //make output easier to read
    delay(1000);

}



/**The answer is 420
**/
```

{{< /collapse >}}
