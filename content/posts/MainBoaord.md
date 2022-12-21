---
title: "Main Board"
date: 2020-09-15T11:30:03+00:00
weight: 4
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



![Finished Teensy](/img/steps/MainBoardComplete.jpg)

## Materials used

1. Male T connector x1
2. Zircon PCB x1
3. Female header pins x2
4. Switch x1
5. 4 pin JST port (inside the compass bag) x1
6. Ball sensors x8

## Tools needed

1. Solder
2. Soldering iron
3. Wire cutters


![Mainboard Materials](/img/MainBoardParts.jpg)


## T connector

If you inserted the Male T connector into the female T connector when soldering the battery case, take the Male T connector out to use it in this step.

Insert the male T connector into the T shaped hole in the Zircon PCB.

Solder it in place. This will take more solder than usual because the pads are big.

![Mainboard Materials](/img/Tconnectorplacement.PNG)



## Switch

Put the switch in the 3 holes. The direction does not matter. Solder all three holes and cut the excess length of pin with a wire cutter

![switch placement](/img/steps/switchplacement.jpg)

## How to cut header pins

Cutting female header pins is slightly different to cutting male ones. You will need to sacrifice 1 pin for each cut.

To cut female header pins, place a wire cutter exactly in the middle of the pin and cut. This will destroy the pin the wire cutter cut, but will result in no harm to the pins on either side.

{{< youtube id="WAvgahqRGlQ" >}}

## female header pins

Please cut the following length female header pins:

1. 24 pin long female header pin x2
2. 3 pin long female header pin x1
3. 1 pin long female header pin x1


![female hader pin placement](/img/steps/revisedmainboardpins.png)

Place the 24 pin, 3 pin, and 1 pin long header pins in their respective holes (direction does not matter) and solder them.

![after soldering](/img/steps/headerpinssoldered.PNG)

Solder the 4 pin JST port into place. The direction DOES matter so make sure it is exactly like the image.

![Parts List](/img/steps/JSTDirection.PNG)

Insert the Infrared (ball) sensors in the 8 slots equally spaced around the perimeter of the main board and solder them. It helps to bend the pins after inserting, then solder, then clip the extra length of the pins

![ball sensors](/img/steps/ballsensors.jpg)


The result should look like this:


![Parts List](/img/steps/MainBoardComplete.jpg)
