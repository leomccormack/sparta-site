---
title: "REAPER compatibility"
description: "Compatibility list of hosting the plug-ins in Reaper."
lead: ""
date: 2025-11-01T08:49:31+00:00
lastmod: 2025-11-01T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 634
toc: true
---

REAPER is a highly flexible DAW for multichannel audio plug-ins, and is the most recommended host for the SPARTA plug-ins. This is due to it supporting an arbitrary number of channels for each track (up to 128), which allows it to support all possible plug-in configurations. 

REAPER also allows the plug-ins to be loaded as VST, LV2, VST3, or AU. However, there are some differences when using these different plug-in formats. Here is a summary of what to expect when hosting these plug-ins on tracks that have more than 64 channels (as tested in REAPER v7.09):
* Note that only the SPARTA plug-ins (i.e., those with the sparta_ prefix) support up to 10th order/128 channels. The other plug-ins in the installer support up to 7th order/64 channels.
* **<span style="color:green">VST</span>** - these versions show up as supporting up to 64 channels (listed as e.g. VST: sparta_ambiBIN (AALTO) (64ch) in the FX window). However, they do actually work up to 128 channels. Note that the plug-ins will warn the user (in the top right of the plug-in window) if there is an insufficient number of input or output channels for the current plug-in configuration.
* **<span style="color:green">LV2</span>** - these show up as supporting 128 channels (e.g., LV2: sparta_ambiBIN (AALTO) (128ch)), and they do actually work up to 128 channels. However, the plug-ins are not able to warn the user (in the top right corner of the plug-in window) if the track has an insufficient number of input/output channels for the current plug-in configuration. Therefore, care must be taken to ensure a sufficient number of channels.
* **<span style="color:red">VST3</span>** - these show up as supporting 128 channels (e.g., VST3: sparta_ambiBIN (AALTO) (128ch)). However, they are actually unpredictable and will only work up to whatever channel layout they feel like doing. They usually cap out at either 24 or 64 channels. In general, VST3 is still not a suitable format for these kind of multi-channel plug-ins. We therefore recommend using the VST (or LV2/AU) versions, if possible.
* **<span style="color:green">AU</span>** - (only for MacOS), these versions work correctly up to 128 channels.