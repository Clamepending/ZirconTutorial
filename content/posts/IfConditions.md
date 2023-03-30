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

find all numbers that divide 21 (factors of 21).

HINT: % will be useful

a % b returns the remainder when a is divided by b

so 9 % 2 will return 1

13 % 3 will return 1

24 % 10 will return 4

## Solution

Answer: 1, 3, 7, 21

{{< collapse summary="show solution" >}}
1, 3, 7, 21
```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    int a = 21;
    
    
    for (int i = 1; i < a + 1; i++) {

        // check if i divides a
        if (a % i == 0) {
            Serial.print(String(i) + ", ");
        }
    }
    Serial.println();

    //make the output readable by slowing it down
    delay(1000);
}

/**
 * 1, 3, 7, 21
**/
    
```

{{< /collapse >}}

