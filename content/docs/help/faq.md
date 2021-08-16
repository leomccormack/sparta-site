---
title: "FAQ"
description: "Answers to frequently asked questions."
lead: "Answers to frequently asked questions."
date: 2021-08-15T08:49:31+00:00
lastmod: 2021-08-15T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 640
toc: true
---

## Which VST2 hosts do you recommend for these plug-ins?

Reaper > MaxMSP = Plogue Bidule > Other.

## What does this slider/button/drop-down menu do?

The vast majority of sliders, toggle buttons, and drop-down menus have detailed tooltips. Simply hover your mouse over the parameter in questions for a few seconds, and the respective tooltip will appear.

## Can I use the plug-ins for commercial purposes?

All of the plug-ins in the SPARTA suite, COMPASS suite, the HO-SIRR application and the CroPaC-Binaural may be used for commercial purposes. 

Their source code may also be used for commercial purposes, provided that you follow the terms of the employed license. For example, for GPLv3 licensed code, commercial use is only possible if the derived works are also open-source and provided under the terms of the same GPLv3 license.

The exception to the above is with the HO-DirAC suite, which can only be used for academic, personal, and/or non-commerical use. For more information, please refer to the [full license terms](../../plugins/hodirac-suite/#license) for the HO-DirAC plug-ins.

## Why are there no VST3 versions of the plug-ins?

Building VST3 versions of the plugins is indeed possible. However, unfortunately, switching from VST2 to VST3 would be a step back in terms of being able to flexibly change the channel layouts and would restrict the maximum Ambisonic order and/or number of channels.

In a nutshell, the VST2 SDK can support flexibly changing the number of channels between 1 and 64 (i.e. up to 7th order Ambisonics, and loudspeaker arrangements of up to 64 channels), whereas the VST3 versions instead supports only up to 24 channels (i.e. 3rd order Ambisonics, and up to 24 loudspeaker setups), which is quite a significant downgrade.

While Steinberg appear to be content with their self-imposed limitation for their own plugins, we are unable to do so as we frequently use these plugins with loudspeaker arrays comprising more than 24 channels (and 4th order+) for our own research and teaching purposes at Aalto University.

If the VST3 SDK is updated, or a VST4 SDK comes along, which restores the features of the VST2 SDK, then we are happy to switch over. However, until then, we will have to stick with the VST2 SDK.

For more information regarding the issue, please refer to the following Steinberg forum posts and GitHub issues:
* [https://sdk.steinberg.net/viewtopic.php?f=4&t=549](https://sdk.steinberg.net/viewtopic.php?f=4&t=549) (18 April 2018)
* [https://sdk.steinberg.net/viewtopic.php?f=4&t=6249](https://sdk.steinberg.net/viewtopic.php?f=4&t=624) (6 December 2018)
* [https://github.com/steinbergmedia/vst3sdk/issues/28](https://github.com/steinbergmedia/vst3sdk/issues/28) (17 January 2019)
* [https://github.com/leomccormack/SPARTA/issues/28](https://github.com/leomccormack/SPARTA/issues/28) (6 March 2021)

## Why are there no AAX versions of the plug-ins?

Unfortunately, the Avid business model is not really compatible with open-source/free plug-in projects.

## Where can I learn more about Ambisonics?

For newcomers to the field, we recommend starting with [this book](https://www.springer.com/gp/book/9783030172060), which is free to download and covers Ambisonics from a practical point-of-view.

## Are there any online communites where I can discuss topics related to spatial audio?

There a number of active Facebook groups, with some of the more popular ones including:
* [Spatial Audio in VR/AR/MR](https://www.facebook.com/groups/SpatialAudioVRARMR)
* [3D, Ambisonic, Binaural & Surround Sound Production](https://www.facebook.com/groups/ambisonic)
* [Ambisonics VR 360 Audio](https://www.facebook.com/groups/Ambisonics.VR.360.Audio)

Outside of these Facebook groups, there is also the [SurSound mailing list](https://mail.music.vt.edu/mailman/listinfo/sursound) and the [SpatialAudio subreddit](https://www.reddit.com/r/SpatialAudio/).

