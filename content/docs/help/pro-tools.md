---
title: "Pro Tools Ultimate compatibility"
description: "Compatibility list of hosting the plug-ins in Pro Tools Ultimate."
lead: ""
date: 2025-11-01T08:49:31+00:00
lastmod: 2025-11-01T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "help"
weight: 635
toc: true
---

AAX versions of the plug-ins can be found under the "Sound Field" category in the Pro Tools Ultimate "Mix" window. They should be added as a "**multichannel plugin**".

Note that compatibility is generally quite high. The plug-ins that receive the grade of <span style="color:YellowGreen">mostly supported</span>, or having <span style="color:orange">limited support</span>, receive these grades usually because of the more restricted multichannel "Track" options in Pro Tools (when compared to e.g. REAPER). However, it is possible that many users won't encounter these restrictions for their specific needs. There are also a few workarounds that can partially restore some plug-in channel layout flexibility, which are described below. In cases where such restrictions prohibit the proper functioning of the plug-in (e.g. the multi-Ambisonic input plug-ins), the affected plug-in will be marked as <span style="color:red">not supported</span>.

It is also highlighted that **certain Pro Tools multichannel bus options will re-order the channels!** For example, if inserting a plug-in with an output configuration of 7.0.6, which has a loudspeaker ordering of [L R C Lss Rss Lsr Rsr Ltf Rtf Ltm Rtm Ltr Rtr], channels 1 through 13, as shown in SPARTA, will be re-ordered by Pro Tools with the following indices: [1 2 3 4 5 10 11 6 7 12 13 8 9]. SPARTA does, however, automatically account for this, by re-arranging the "Pro Tools 7.0.6" output configuration preset to be [L R C Lss Rss **Ltm Rtm Lsr Rsr Ltr Rtr Ltf Ltr**] for channels 1 through 13. This is also why the "Pro Tools 7.0.6" **input** configuration preset (in e.g. sparta_ambiENC) is ordered differently to the "Pro Tools 7.0.6" **output** configuration preset (in e.g. sparta_ambiDEC). If the plug-in configuration and bus insert configurations match, then this should not be an issue. However, we believe that users should be made aware of this particular Pro Tools quirk, and should also double check their loudspeaker channel routing (using e.g. sparta_panner to pan noise to each loudspeaker/channel), before working with the plug-ins. If the channel ordering is somehow different, (for example, if the user has configured a custom layout via Setup->I/O), then the user can "export" and "import" loudspeaker configuration .json files via the interface of the relevant SPARTA plug-ins. 

Note that nearly all compatibility issues described below would be resolved if Pro Tools were to be updated to support "discrete" arbitrary 1-64 (or 1-128) channel "Tracks". The remaining compatibility issues will be gradually addressed through future plug-in patches, and the below list will be updated periodically. 

Please file a GitHub [issue](https://github.com/leomccormack/SPARTA/issues) if you encounter a problem/limitation that is not described below.

All testing is currently conducted in Pro Tools (Developer) version 25.12.0.

## SPARTA

* **sparta_ambiBIN** - <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics/Stereo)" insert on an Ambisonics "Track". Although, 8th order (and higher) busses are not available in Pro Tools.
* **sparta_ambiDEC** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel output formats that Pro Tools supports. If the plug-in is added as a e.g. "(5th order Ambisonics/7.0.6)" insert, then the user must also set the playback configuration to "ProTools 7.0.6" in the plug-in. LFE channels are not rendered by the plug-in. If the plug-in is added as a e.g. "(5th order Ambisonics/5.1)" insert, then the following warning message is displayed in the top right of the plug-in interface: _"LFE channels are not supported by this plug-in"_.
* **sparta_ambiDRC** - <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics)" insert on an Ambisonics "Track". The only limitation is that 8th order (and higher) Tracks are not supported in Pro Tools.
* **sparta_ambiENC** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel input formats that Pro Tools supports. If the plug-in is added as a e.g. "(5.0/5th order Ambisonics)" insert, then the user must also set the input configuration to "ProTools 5.0" in the plug-in. LFE channels are not rendered by the plug-in. If the plug-in is added as a e.g. "(5.1/5th order Ambisonics)" insert, then the following warning message is displayed in the top right of the plug-in interface: _"LFE channels are not supported by this plug-in"_.
* **sparta_ambiRoomSim** - <span style="color:YellowGreen">mostly supported</span>. The main limitation is that this plug-in supports outputting multiple Ambisonic receiver simulations (stacked ontop of eachother, e.g. output channels 1-16 corresponding to the first third-order receiver, and channels 17-32 corresponding to the second third-order receiver). However, Pro Tools can only be configured to output the Ambisonics signals of a single receiver. 
* **sparta_array2SH** - <span style="color:orange">limited support</span>. Due to Pro Tools requiring specific fixed input/output channel configurations, the user will need to work around this limitation. For example, if the user wishes to encode a tetrahedral microphone array recording into 1st order ambisonics, then they can add the plug-in as a e.g. "(Quad/1st order Ambisonics)" insert. Support for higher-order Ambisonic arrays is more challenging. For example a Zylia array (19 channels) or Eigenmike (32 channels) recording will need to have extra (zero) channels appended to them, in order to fit onto e.g. 4th order or 5th order Ambisonics "Tracks", respectively. However, if the user e.g. uses a 7.0.6 bus for encoding a 12 channel microphone array recording, note that Pro Tools re-orders the channels! and so the user must be very careful.  
* **sparta_beamformer** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel output formats that Pro Tools supports. 
* **sparta_binauraliser** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel input formats that Pro Tools supports. If the plug-in is added as a e.g. "(5.0/Stereo)" insert, then the user must also set the input configuration to "ProTools 5.0" in the plug-in. LFE channels are not rendered by the plug-in. If the plug-in is added as a e.g. "(5.1/Stereo)" insert, then the following warning message is displayed in the top right of the plug-in interface: _"LFE channels are not supported by this plug-in"_.
* **sparta_binauraliser_nf** - <span style="color:YellowGreen">mostly supported</span>. Same notes as for sparta_binauraliser. 
* **sparta_decorrelator** - <span style="color:green">fully supported</span>, since it applies the same processing for each channel independently. The only limitation is that channel counts more than 64 are not supported in Pro Tools.
* **sparta_dirass** -  <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics)" insert on an Ambisonics "Track".
* **sparta_matrixConv** - <span style="color:orange">limited support</span>. Due to Pro Tools requiring specific fixed input/output channel configurations, the user will likely need to try and work around this limitation for most intended applications of the plug-in.
* **sparta_multiConv** - <span style="color:orange">limited support</span>. Same notes as sparta_matrixConv.
* **sparta_6DoFConv** - <span style="color:orange">limited support</span>. Same notes as sparta_matrixConv.
* **sparta_pitchShifter** - <span style="color:green">fully supported</span>, since it applies the same processing for each channel independently. The only limitation is that channel counts more than 64 are not supported in Pro Tools.
* **sparta_powermap** -  <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics)" insert on an Ambisonics "Track".
* **sparta_rotator** -  <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics)" insert on an Ambisonics "Track".
* **sparta_sldoa** -  <span style="color:green">fully supported</span> when added as a e.g. "(5th Order Ambisonics)" insert on an Ambisonics "Track".
* **sparta_spreader** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel output formats that Pro Tools supports. 
* **sparta_trackerTest** - <span style="color:red">not supported</span>. Distributed only as VST and for Windows due to its OptiTrack dependencies.

## COMPASS

* **compass_6DoF** - <span style="color:red">not supported</span>, since it requires two (or more) Ambisonic busses to be stacked ontop of each other (e.g. inputs 1-9 corresponding to first 2nd order receiver, and inputs 10-18 corresponding to the second 2nd order receiver). However, no such busses (or workarounds) exist in Pro Tools. 
* **compass_binaural** - <span style="color:green">fully supported</span> when added as a e.g. "(3rd Order Ambisonics/Stereo)" insert on an Ambisonics "Track". 
* **compass_binauralVR** - <span style="color:YellowGreen">mostly supported</span> when added as a e.g. "(3rd Order Ambisonics/Stereo)" insert on an Ambisonics "Track". To support two simultaneous listeners, the plug-in can be added as "(3rd Order Ambisonics/Quad)". However, for three or four listeners, there are no suitable 6 or 8 channel busses that do not also re-order the channels.
* **compass_decoder** - <span style="color:YellowGreen">mostly supported</span>. Works only with multichannel output formats that Pro Tools supports. If the plug-in is added as a e.g. "(1st order Ambisonics/7.0.6)" insert, then the user must also set the playback configuration to "ProTools 7.0.6" in the plug-in. LFE channels are not rendered by the plug-in. If the plug-in is added as a e.g. "(1st order Ambisonics/5.1)" insert, then the following warning message is displayed in the top right of the plug-in interface: _"LFE channels are not supported by this plug-in"_.
* **compass_gravitator** - <span style="color:green">fully supported</span> when added as a e.g. "(3rd Order Ambisonics)" insert on an Ambisonics "Track". 
* **compass_sidechain** - <span style="color:red">not supported</span>. Requires two Ambisonic busses to be stacked ontop of each other (e.g. inputs 1-16 corresponding to first 3rd order scene, and inputs 17-32 corresponding to the second 3rd order scene). However, no such busses (or workarounds) exist in Pro Tools.
* **compass_spatedit** - <span style="color:orange">limited support</span>. Requires two instances, one with Ambisonics input and a variable number of output channels, and the other with a variable number of input channels and Ambisonics output. The number of tracked objects therefore needs to be capped to 1-4.
* **compass_tracker** - <span style="color:YellowGreen">mostly supported</span>. Works well when added as a e.g. "(3rd Order Ambisonics/Stereo)" insert, when outputting binauralised beamformers, or as a e.g. "(3rd Order Ambisonics)" insert if not steering any beamformers. However, if steering beamformers and not binauralising them, then the number of tracked objects is capped to 1-4 (Mono, Stereo, LRC, Quad), or will risk being re-ordered by Pro Tools.
* **compass_upmixer** - <span style="color:green">fully supported</span>. Works well when added as a e.g. "(1st Order Ambisonics/3rd order Ambisonics)" insert.

## HO-DirAC

* **hodirac_binaural** - <span style="color:green">fully supported</span>. Fully supported when added as a e.g. "(3rd Order Ambisonics/Stereo)" insert on an Ambisonics "Track". 
* **hodirac_decoder** - <span style="color:YellowGreen">mostly supported</span>. Mostly supported. Works only with multichannel output formats that Pro Tools supports. If the plug-in is added as a e.g. "(1st order Ambisonics/7.0.6)" insert, then the user must also set the playback configuration to "ProTools 7.0.6" in the plug-in. LFE channels are not rendered by the plug-in. If the plug-in is added as a e.g. "(1st order Ambisonics/5.1)" insert, then the following warning message is displayed in the top right of the plug-in interface: _"LFE channels are not supported by this plug-in"_.
* **hodirac_upmixer** - <span style="color:green">fully supported</span>. Works well when added as a e.g. "(1st Order Ambisonics/3rd order Ambisonics)" insert.

## Other

* **cropac_binaural** - <span style="color:green">fully supported</span> when added as a e.g. "(1st Order Ambisonics/Stereo)" insert on an Ambisonics "Track".
* **hades_renderer** - <span style="color:YellowGreen">mostly supported</span>. However, it depends on the number of microphones in the array. Note that 2-4 microphone array recordings (loaded onto a Stereo, LRC, or Quad input channel bus, with stereo output) are safe, since they are not re-ordered by Pro Tools. However, higher-channel count microphone arrays require care, in order to make sure Pro Tools does not re-order the channels.
* **HOSIRR** - <span style="color:green">fully supported</span>, since it's more of a standalone application. It doesn't process audio, so the bus configuration does not matter.
* **UltrasonicSuperHearing** - <span style="color:red">not supported</span>. There is no suitable channel configuration for this plug-in in Pro Tools.

## Known bugs

When testing in Pro Tools Developer version 25.6.0, the following cryptic error message was shown during the second (and third etc.) start-up, when more than approximately 30 3rd-party plug-ins were loaded: "Could not complete your request because Assertion in "/Users/autobld/gitlabci/PT3PDEV/ProTools/App/PtApp/PtApp_AuditionMgr.cpp", line 2557.". This was also the case when installing non-SPARTA plug-ins. 
- Solution: Removing arbitrary plug-ins so that there are fewer than 30 plug-ins in total "fixed" the issue. After months of trail and error to try and isolate the real issue, to no avail, updating to Pro Tools Developer version 25.12.0 fixed the issue completely... We therefore recommend using the most recent version of Pro Tools. 