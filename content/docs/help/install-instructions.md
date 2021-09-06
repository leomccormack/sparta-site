---
title: "Install instructions"
description: "Instructions on how to install the included VST plug-ins."
lead: "Instructions on how to install the included VST plug-ins."
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

## MacOS (x86) users

MacOS users can simply unzip and run the installer. 

For MacOS versions 10.15 and above, you may need to give explicit permission for the installer to run via Settings->Security->"Open anyway". In rare cases, you may need to use the following command in the terminal for each plug-in:

```
sudo xattr -d com.apple.quarantine /Library/Audio/Plug-Ins/VST/AmbiBIN.vst
...
sudo xattr -d com.apple.quarantine /Library/Audio/Plug-Ins/VST/Spreader.vst
... etc.
```

The installer places the VSTs in the following folder:
```
/Library/Audio/Plug-Ins/VST/
```
And also installs the following files:
```
/usr/local/lib/libsaf_mkl_custom_lp64.dylib
/usr/local/lib/libsaf_ipp_custom.dylib
```

To uninstall, simply delete these files.


## Windows (x86) users

Windows users can simply unzip and run the installer. 

The installer places the VSTs in the following folder:
```
C:/Program Files/VSTPlugins
```
And also installs the following files:
```
/Windows/System32/saf_mkl_custom_lp64.dll
/Windows/System32/saf_ipp_custom.dll
```
To uninstall, simply delete these files.

## Linux (x86) users

Linux users can download, unzip and copy the plugins into any folder that is scanned by the VST host for VST plug-ins. For example:
```
~/.vst
```
The following included files must then also be copied into:
```
/usr/local/lib/libsaf_mkl_custom_lp64.so
/usr/local/lib/libsaf_ipp_custom.so
```
To uninstall, simply delete these files.


## Raspberry Pi and ARM users

{{< alert icon="👉" text="Please note that only the Raspberry Pi 3B and Raspberry Pi 4 have been tested by the developers" />}}

There are currently no pre-built binaries for Raspberry Pi or ARM-based architectures, however, there are build instructions, which can be found [here](https://github.com/leomccormack/SPARTA/blob/master/docs/RaspberryPi_instructions.md).
