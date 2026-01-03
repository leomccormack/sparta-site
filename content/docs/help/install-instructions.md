---
title: "Install instructions"
description: "Instructions on how to install the included VST plug-ins."
lead: ""
date: 2021-08-15T13:26:54+01:00
lastmod: 2021-08-15T13:26:54+01:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 600
toc: true
---

## MacOS (ARM/x86_64) 

MacOS users can simply run the installer(s). 

The installer(s) place the VST, LV2, VST3, AU, and AAX plug-ins in the following respective folders:
```
/Library/Audio/Plug-Ins/VST/
/Library/Audio/Plug-Ins/LV2/
/Library/Audio/Plug-Ins/VST3/
/Library/Audio/Plug-Ins/Components/
/Library/Application Support/Avid/Audio/Plug-Ins/
```

To uninstall, simply delete these files.

## Windows (x86_64) 

Windows users can simply run the installer(s). 

The installer places the VST, LV2, and VST3 plug-ins in the following respective folders:
```
C:/Program Files/Steinberg/VSTPlugins
C:/Program Files/Common Files/LV2
C:/Program Files/Common Files/VST3
```
And also installs the following file:
```
/Windows/System32/saf_mkl_custom_lp64.dll
```
To uninstall, simply delete these files.

## Linux (x86_64) 

Linux users can download, unzip and copy the plug-ins into any folder that is scanned by the VST, LV2, and/or VST3 host. For example:

```
~/.vst
~/.lv2
~/.vst3
```

The following included file **must also be copied** into this folder:
```
/usr/local/lib/libsaf_mkl_custom_lp64.so
```

To uninstall, simply delete these files.


## Raspberry Pi (ARM)

Please note that only the Raspberry Pi 3B and Raspberry Pi 4 have been tested by the developers.

There are currently no pre-built binaries for Raspberry Pi or ARM-based architectures. However, build instructions can be found [here](https://github.com/leomccormack/SPARTA/blob/master/docs/RaspberryPi_instructions.md).
