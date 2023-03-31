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

modify the variable x so that the if statement prints "correct!"

```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    int x = 420;
    
    
    if (x == 21) {
        Serial.println("correct!");
    } else {
        Serial.println("keep trying");
    }

    //make the output readable by slowing it down
    delay(1000);
}

```

HINT: == checks if two numbers are equal.
```C++
3 == 3 // THIS IS TRUE
```
```C++
3 == 4// THIS IS FALSE
```

HINT 2:

Change the number 420 to another number


## Solution

{{< collapse summary="show solution" >}}
```C++
#include <Arduino.h>

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   

void loop() {
    int x = 21;
    
    
    if (x == 21) {
        Serial.println("correct!");
    } else {
        Serial.println("keep trying");
    }

    //make the output readable by slowing it down
    delay(1000);
}

```

{{< /collapse >}}

