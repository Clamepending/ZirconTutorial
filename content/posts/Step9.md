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

1. Zircon x1
2. Teensy from Part 2 x1
3. Battery from Part 1 x1
4. AA battery x4 (not included)
5. Compass x1

## Tools needed

1. voltmeter

![Motor Materials](/img/HardwareCheckParts.jpg)

## Insert teensy

Be careful with this step. Make sure not to bend any pins and make sure all pins are going into the slots they are supposed to.

Plug the teensy into the female header pins on the Zircon furthest to the right.

![Motor Materials](/img/steps/putTeensyIn.jpg)

## Double Check

The reason there are extra female header pins on the Zircon that are unused is because the Zircon is compatible with the teensy 3.5 and 3.6 as well, which are longer than the LC that is included in the kit.

Inserting the teensy into the wrong slot or pins not going where they are supposed to can damage the kit, so please double check if the teensy is inserted in the correct spot and all pins are inserted (including the inner 3).

![inserting pin](/img/steps/SecondteensyInsertedpic.jpg)

## Battery Check

Insert the AA batteries into the battery holder. Set your voltmeter to measure voltage (around 6 volts if there is a setting on your voltmeter) Make sure the black probe of the voltmeter is on the COM port of the voltmeter and the red probe is on VΩmA.

Place the black probe into the vertical and black part of the T connector of the battery case. Place the red probe into the horizontal and red part of the T connector of the battery case.

The voltmeter should read POSITIVE 6 volts. If it reads negative, please unsolder and swap the red and black wires of the battery case. As a doublecheck, swapping the voltmeter probes should show NEGATIVE 6 volts. As an additional reference, here is a lipo battery with a T connector. The colors of the battery wires (red and black) connected to the T connector should be exactly like your battery case.

![soldered motors](/img/steps/DoublecheckBattery.jpg)

## Magic smoke

Now that you checked the battery is made correctly, plug it into the Zircon through the T connector. If the line sensors and teensy have not turned on (shown by an led),flip the big switch.

Take the compass sensor and connect it to the Zircon through its 4 pin cable. The compass should light up with a green LED. If the LEDs do not light up, unplug the battery and check if it is hot. Make sure you plugged in everything in the correct slot, line sensors are in the exact orientation they should be, and the 4 pin JST port is in the correct direction.


![Finished Motors](/img/mainPhoto.jpg)


Congratulations!

hardware is done… for now >:)

next up: software

