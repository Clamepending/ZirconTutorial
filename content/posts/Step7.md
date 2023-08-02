---
title: "STEP 7"
date: 2020-09-15T11:30:03+00:00
weight: 7
# aliases: ["/first"]
tags: ["hardware"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Mounting"
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
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

| No. | Part Name                      | Image                                            |
|-----|--------------------------------|--------------------------------------------------|
| 1.  | Motor and Omniwheel from Part 5 x3 | ![Motor and Omniwheel](/img/motor_omniwheel.jpg) |
| 2.  | M3 Bolts x12                   | ![M3 Bolts](/img/screws.jpg)                     |
| 3.  | M3 Nuts x12                    | ![M3 Nuts](/img/nuts.jpg)                       |

## Tools needed

| No. | Tool Name                       | Image                                               |
|-----|---------------------------------|-----------------------------------------------------|
| 1.  | Solder                          | ![Solder](/img/solder.jpg)                           |
| 2.  | Soldering Iron                  | ![Soldering Iron](/img/iron.jpg)            |
| 3.  | Phillips Head Screwdriver        | ![Phillips Head Screwdriver](/img/screwdriver.jpg)    |
| 4.  | Pliers               | ![Pliers](/img/pliers.jpg)                           |


![Motor Materials](/img/cuttingbottom.PNG)


To mount the motors, we need as flat of a board as possible underneath where the motors will sit.

Use a wire cutter to cut any pins sticking out from under the Zircon board. Be careful not to damage the silkscreen (the green or black part of the Zircon board).

(short video showing cutting)

## Secure motors

We will repeat the next steps 3 times for each motor. For this step, be sure not to overtighten the bolts and dig into the PCB. Tighten them comfortably but not too much. 

Get four m3 bolts and m3 nuts. Secure the motor onto the Zircon board with the 4 bolts through the holes in the black casing.

![securing motor](/img/steps/securingmotor.PNG)

(insert finished picture)

## Solder motor wires

Solder the motor wires into their respective pins Accidentally swapping the pins of the same motor is fine. The result would be the motor will spin in the opposite way than it is commanded (keep that in mind when programming).

Accidentally swapping pins from different motors is not fine, so if that happens please unsolder carefully and correct it.

Repeat these steps for the other 2 motors.

(reshoot video with new version because pinout is different)

{{< youtube id="RKKadLGrtvk?rel=0" >}}

The result should look like this

(retake picture with new pinout)
![soldered motors](/img/motorwiressoldered.PNG)
