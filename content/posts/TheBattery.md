---
title: "The Battery"
date: 2020-09-15T11:30:03+00:00
weight: 2
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



![Parts List](/img/PartsList.jpg)

## Materials used

1. MAIN PCB X1
2. FEMALE HEADER PINS X2   
3. SWITCH X1
4. MALE T CONNECTOR X1
5. FEMALE T CONNECTOR X1
6. AA BATTERY HOLDERX1
7. TEENSY LC X1
8. MALE HEADER PINS X2
9. MOTORS X3
10. MOTOR MOUNT X3
11. OMNIWHEELS X3
12. WIRE X3
13. 4 PIN SOCKET (I2C) X1
14. LINE SENSORS X3
15. M3 BOLTS X36
16. M3 NUTS X12
17. M3 STANDOFFS X12

## Tools needed

1. SOLDERING IRON
2. SOLDER
3. BIG AND SMALL PHILLIPS HEAD SCREW DRIVER
4. PLIERS
5. WIRE CUTTERS
6. VOLTMETER



# Soldering

If you do not know how to solder, it is recommended you practice first with something like https://www.sparkfun.com/products/14635 or a spare board before this.

Soldering is used to make an electrical connection between two parts. It involves melting the solder with the soldering iron (at 250° - 350°C) and touching the molten solder onto where the connection is needed. There are many excellent soldering tutorials on youtube like the one below.

Hint: To keep the female t connector from deforming, it is a good idea to plug the male one in to keep the shape while soldering.

{{< youtube id="VxMV6wGS3NY" >}}


Solder the black wire to the horizontal pin and red wire to the vertica pin of the T connector.

![Battery Connector](/img/steps/BatteryTConnectorBack.jpg)

The result should look like this:

![Parts List](/img/steps/TheBattery.jpg)
