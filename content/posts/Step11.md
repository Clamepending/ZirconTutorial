---
title: "STEP 11"
date: 2020-09-15T11:30:03+00:00
weight: 11
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Move a motor"
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

Lets move a motor!
    
{{< youtube id="xylDcAshLSQ" >}}

```C++
#include <Arduino.h>
#include <zirconLib.h>


void setup(void)
{
  Serial.begin(115200);
  InitializeZircon();

}


void loop(void)
{
    motor1(100, 0);
}
```


{{< youtube id="7tNuw-rc-f8" >}}

{{< youtube id="HrnbmBG9HAQ" >}}




