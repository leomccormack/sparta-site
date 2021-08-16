---
title: "Where to find?"
description: "Overview of the plug-in source code."
lead: ""
date: 2021-08-16T08:48:57+00:00
lastmod: 2021-08-16T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "sourcecode"
weight: 400
toc: true
---

The collection of plug-ins included in the SPARTA installer are the culmination of numerous software projects.

## Frameworks and SDKs

All plug-ins included in the SPARTA suite employ the open-source **JUCE framework** for their graphical user-interface (GUI) and for wrapping arround the **VST2 SDK**. The open-source **Spatial_Audio_Framework** is then used for developing the internal spatial audio signal processing.

* Source code for the [Spatial_Audio_Framework →](https://github.com/leomccormack/Spatial_Audio_Framework)
* Source code for the [JUCE framework →](https://github.com/juce-framework/JUCE)
* Download link for the [VST2 SDK →](https://web.archive.org/web/20181016150224/https://download.steinberg.net/sdk_downloads/vstsdk3610_11_06_2018_build_37.zip)

Both frameworks are also accompanied by extensive online documentation:
* Documentation for the [Spatial_Audio_Framework →](https://leomccormack.github.io/Spatial_Audio_Framework)
* Documentation for the [JUCE framework →](https://docs.juce.com/master/modules.html)
 
## SPARTA suite source code

The source code for the SPARTA plug-ins is made available under the [GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/) license. However, it should be noted that the repository contains only code for the plug-in GUIs, with the internal signal processing inherited directly from the "examples" ([ISC license](https://choosealicense.com/licenses/isc/)) found in the Spatial_Audio_Framework.

* Source code for the [SPARTA suite →](https://github.com/leomccormack/SPARTA)
* Documentation for the [Spatial_Audio_Framework examples →](https://leomccormack.github.io/Spatial_Audio_Framework/examples.html)

## HO-SIRR source code

The source code for the HO-SIRR application is made available under the [GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/) license. It is essentially a direct C port of the MATLAB toolbox code with JUCE GUI.

* Source code for the [HO-SIRR application →](https://github.com/leomccormack/HO-SIRR-GUI)
* Source code for the [HO-SIRR MATLAB toolbox →](https://github.com/leomccormack/HO-SIRR)

## CroPaC-Binaural source code

The source code for the CroPaC-Binaural decoder is made available under the [GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/) license.

* Source code for the [CroPaC-Binaural decoder →](https://github.com/leomccormack/CroPaC-Binaural)