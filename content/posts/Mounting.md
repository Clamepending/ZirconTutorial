---
title: "Mounting"
date: 2020-09-15T11:30:03+00:00
weight: 7
# aliases: ["/first"]
tags: ["first"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
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



![Finished Motors](/img/motorwiressoldered.PNG)

## Materials used

1. Motor and omniwheel from part 5 x3
2. M3 bolts x12
3. M3 nuts x12

## Tools needed

1. Solder
2. Soldering iron
3. Phillips head screwdriver
4. Pliers (optional)


![Motor Materials](/img/cuttingbottom.PNG)


To mount the motors, we need as flat of a board as possible underneath where the motors will sit.

Use a wire cutter to cut any pins sticking out from under the Zircon board. Be careful not to damage the silkscreen (the green or black part of the Zircon board).

## Secure motors

We will repeat the next steps 3 times for each motor. For this step, be sure not to overtighten the bolts and dig into the PCB. Tighten them comfortably but not too much. Get 4 m3 bolts (the larger ones) and m3 nuts. Secure the motor onto the Zircon board with the 4 bolts through the holes in the black casing.

![inserting pin](/img/steps/securingmotor.PNG)

## Solder motor wires

Solder the motor wires into their respective pins Accidentally swapping the pins of the same motor is fine. The result would be the motor will spin in the opposite way than it is commanded (keep that in mind when programming).

Accidentally swapping pins from different motors is not fine, so if that happens please unsolder carefully and correct it.

Repeat these steps for the other 2 motors.

{{< youtube id="RKKadLGrtvk" >}}

The result should look like this

![soldered motors](/img/motorwiressoldered.PNG)
