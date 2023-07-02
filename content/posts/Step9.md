---
title: "STEP 9"
date: 2020-09-15T11:30:03+00:00
weight: 9
# aliases: ["/first"]
tags: ["hardware"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Hardware Check"
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



![Finished Motors](/img/mainPhoto.jpg)

## Materials used

| No. | Part Name                 | Image                                       |
|-----|---------------------------|---------------------------------------------|
| 1.  | Zircon x1                 | ![Zircon](/img/mainPhoto.jpg)                   |
| 2.  | Teensy x1     | ![Teensy](/img/teensy.jpg)                   |
| 3.  | Battery from Part 1 x1    | ![Battery](/img/battery.jpg)                 |
| 4.  | AA Battery x4 (not included) | ![AA Battery](/img/aabattery.jpg)           |
| 5.  | Compass x1                | ![Compass](/img/compass.jpg)                 |


## Insert teensy

Be careful with this step. Make sure not to bend any pins and make sure all pins are going into the slots they are supposed to.

THE DIRECTION DOES MATTER, so make sure you put it in the correct way.

(retake picture with teensy 4.1)

![Motor Materials](/img/steps/putTeensyIn.jpg)

## Double Check

Double check if the teensy is put in the right way.

(picture)

## Battery Check

Get your battery case.

![soldered motors](/img/emptyBatterycase.jpg)

Insert the AA batteries into the battery holder. 

(image of loaded battery case)

## Magic smoke

Check if your battery case is soldered correctly (make sure you did not mix up the red and black wires!). 

Plug it into the Zircon through the T connector. If the line sensors and teensy have not turned on (shown by an led), flip the big switch.

The line snesors should light up.

Take the compass sensor and connect it to the Zircon through its 4 pin cable. The compass should light up with a green LED. If the LEDs do not light up, unplug the battery and check if it is hot. Make sure you plugged in everything in the correct slot, line sensors are in the exact orientation they should be, and the 4 pin JST port is in the correct direction.


![Finished Motors](/img/mainPhoto.jpg)


Congratulations!

hardware is done… for now >:)

next up: software

