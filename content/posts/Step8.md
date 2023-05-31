---
title: "STEP 8"
date: 2020-09-15T11:30:03+00:00
weight: 8
# aliases: ["/first"]
tags: ["hardware"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Line Sensors"
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

1. M3 Metal female female standoffs x12
2. M3 bolts x24
3. Line sensor x3

## Tools needed

1. Screw driver

![Motor Materials](/img/linesensorparts.jpg)


The line sensor board has 4 holes, of which 1 is placed closer to the edge. There should be 3 of the same shape on the Zircon board.

Use 4 bolts and 4 standoffs to sandwich the line sensor. The bolts should be screwed in from the side with electrical components (side DOES matter)

## Prepare line sensor

We will repeat the next steps 3 times for each motor. For this step, be sure not to overtighten the bolts and dig into the PCB. Tighten them comfortably but not too much. Get 4 m3 bolts (the larger ones) and m3 nuts. Secure the motor onto the Zircon board with the 4 bolts through the holes in the black casing.

![inserting pin](/img/steps/linesensorsingle.jpg)

## Secure line sensor

Attach the sensor to the Zircon board with 4 more bolts. The standoffs should be straight. If not, please make sure you put the line sensor in the correct orientation and facing down.

Repeat 2 more times.

![soldered motors](/img/steps/MountedLinesensor.jpg)

The result should look like this

![soldered motors](/img/steps/FinishedLineSensor.jpg)
