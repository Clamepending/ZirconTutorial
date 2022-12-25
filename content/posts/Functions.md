---
title: "functions"
date: 2020-09-15T11:30:03+00:00
weight: 18
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Step 17"
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

create a function that takes in n and prints out "Your Name n" with n in that string replaced with the number n

then use that function to print "Your Name n" with n going from 1 to 100

output should look like:

Your Name 1

Your Name 2

...

Your Name 99

Your Name 100

## Solution


{{< collapse summary="show solution" >}}

```C++
#include <Arduino.h>


//MAKE SURE TO DEFINE YOUR FUNCTIONS AT THE TOP
//because you need to define them before you use them
//or else you will get an error like this:
//error: 'countFromNto10N' was not declared in this scope


void PrintMyName(int n){
  Serial.println("Your Name " + String(n));
}

void setup() {
    // put your setup code here, to run once:

    Serial.begin(9600);

}   


void loop() {

    for(int i = 1; i < 101; i++){
      PrintMyName(i);
    }
    
    delay(1000);
}



/**
 * Output: 
 Your Name 1
 Your Name 2
 Your Name 3
 Your Name 4
 Your Name 5
 Your Name 6
 Your Name 7
 Your Name 8
 Your Name 9
 Your Name 10
 Your Name 11
 Your Name 12
 Your Name 13
 Your Name 14
 Your Name 15
 Your Name 16
 Your Name 17
 Your Name 18
 Your Name 19
 Your Name 20
 Your Name 21
 Your Name 22
 Your Name 23
 Your Name 24
 Your Name 25
 Your Name 26
 Your Name 27
 Your Name 28
 Your Name 29
 Your Name 30
 Your Name 31
 Your Name 32
 Your Name 33
 Your Name 34
 Your Name 35
 Your Name 36
 Your Name 37
 Your Name 38
 Your Name 39
 Your Name 40
 Your Name 41
 Your Name 42
 Your Name 43
 Your Name 44
 Your Name 45
 Your Name 46
 Your Name 47
 Your Name 48
 Your Name 49
 Your Name 50
 Your Name 51
 Your Name 52
 Your Name 53
 Your Name 54
 Your Name 55
 Your Name 56
 Your Name 57
 Your Name 58
 Your Name 59
 Your Name 60
 Your Name 61
 Your Name 62
 Your Name 63
 Your Name 64
 Your Name 65
 Your Name 66
 Your Name 67
 Your Name 68
 Your Name 69
 Your Name 70
 Your Name 71
 Your Name 72
 Your Name 73
 Your Name 74
 Your Name 75
 Your Name 76
 Your Name 77
 Your Name 78
 Your Name 79
 Your Name 80
 Your Name 81
 Your Name 82
 Your Name 83
 Your Name 84
 Your Name 85
 Your Name 86
 Your Name 87
 Your Name 88
 Your Name 89
 Your Name 90
 Your Name 91
 Your Name 92
 Your Name 93
 Your Name 94
 Your Name 95
 Your Name 96
 Your Name 97
 Your Name 98
 Your Name 99
 Your Name 100
**/
```

{{< /collapse >}}
