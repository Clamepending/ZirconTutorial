---
title: "Variables, Comments, Loops"
date: 2020-09-15T11:30:03+00:00
weight: 15.4
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

Print "dog n" with n in that string replaced with numbers from 1 to 100.

only print powers of 2. (multiply by 2 instead of adding each time)

repeat once every second.

output should look like:

dog 1

dog 2

dog 4

dog 8

dog 16

dog 32

dog 64

## Solution

{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>

    void setup() {
        // put your setup code here, to run once:
    
        Serial.begin(9600);
    
    }   
    
    void loop() {
    
        for(int i = 1; i < 101; i = i * 2){
            Serial.println("dog" + String(i));
        }
        
        
        delay(1000);
    }

{{< /collapse >}}

