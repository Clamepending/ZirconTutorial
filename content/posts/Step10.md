---
title: "STEP 10"
date: 2020-09-15T11:30:03+00:00
weight: 10
# aliases: ["/first"]
tags: ["software"]
author: "Mark Ogata"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Software Setup"
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

We will now be programming the Zircon.

Your Zircon should look like this

![Finished Motors](/img/mainPhoto.jpg)

Disconnect the compass sensor. We will connect it back later when we need it. (Having it connected will make the robot go through a calibration step at the start, while not connecting it will bypass it)

Watch the video to get started on the first step: downloading a code editor.

## Materials used

| No. | Part Name                    | Image                                            |
|-----|------------------------------|--------------------------------------------------|
| 1.  | Finished Zircon x1           | ![Finished Zircon](/img/mainPhoto.jpg)      |
| 2.  | USB to Micro USB Cable x1    | ![USB to Micro USB Cable](/img/usbcable.jpg)      |
| 3.  | Computer x1                  | ![Computer](/img/computer.jpg)                    |

## VS Code and platformio

{{< youtube id="xylDcAshLSQ?rel=0" >}}

[Download VS Code](https://code.visualstudio.com/download)


{{< youtube id="7tNuw-rc-f8" >}}

{{< youtube id="HrnbmBG9HAQ" >}}

```C++
lib_deps = clamepending/ZirconLib
```


