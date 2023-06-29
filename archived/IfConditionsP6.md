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

find all numbers that divide 21 (factors of 21).

HINT: Use a for loop and if statement with %.

reminder:

% returns the remainder:
```C++
22 % 3 //returns 1
```
```C++
31 % 7 //returns 3
```
```C++
9 % 3 // returns 0
```



## Solution

Answer: 1, 3, 7, 21

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    
    for (int i = 1; i < 22; i++) {

        // check if i divides 21
        if (21 % i == 0) {
            Serial.print(String(i) + ", ");
        }
    }
    Serial.println();

    //make the output readable by slowing it down
    delay(1000);
}

```


{{< /collapse >}}

