---
title: "Overview"
description: "What's included in the SPARTA installer?"
lead: "SPARTA is a collection of flexible VST/LV2 audio plug-ins for spatial audio production, reproduction and visualisation, developed primarily by members of the Acoustics Lab at Aalto University, Finland."
date: 2021-08-15T08:48:57+00:00
lastmod: 2021-08-15T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 100
toc: true
---

The SPARTA installer also includes the COMPASS suite, the HO-DirAC suite, CroPaC Binaural Decoder, and the HO-SIRR room impulse response renderer. 
These plug-ins employ parametric processing and are signal-dependent. They aim to go beyond conventional linear Ambisonics algorithms, used by the baseline SPARTA plug-ins, by extracting meaningful parameters over time and subsequently employing them to map the input to the output in an adaptive and informed manner.

[**Example REAPER projects may be found here**](https://github.com/leomccormack/sparta-reaper-examples).

## All included plug-ins

### SPARTA 

[SPARTA Suite →]({{< relref "sparta-suite" >}})

* [**sparta_ambiBIN**](../sparta-suite/#ambibin) - A binaural ambisonic decoder (up to 10th order) with a built-in SOFA loader and head-tracking support via OSC messages. Includes: Least-Squares (LS), spatial re-sampling (SPR, virtual loudspeakers), time-alignment (TA), and magnitude least-squares (Mag-LS) decoding options.
* [**sparta_ambiDEC**](../sparta-suite/#ambidec) - A frequency-dependent loudspeaker ambisonic decoder (up to 10th order) with user specifiable loudspeaker directions (up to 128), which may be optionally imported via JSON configuration files. Includes: All-Round (AllRAD), Energy-Preserving (EPAD), Spatial (SAD), and Mode-Matching (MMD) ambisonic decoding options. The loudspeaker signals may also be binauralised for headphone playback.
* [**sparta_ambiDRC**](../sparta-suite/#ambidrc) - A frequency-dependent dynamic range compressor (DRC) for ambisonic signals (up to 10th order).
* [**sparta_ambiENC**](../sparta-suite/#ambienc) - An ambisonic encoder/panner (up to 10th order), with support for up to 128 input channels; the directions for which may also be imported via JSON configuration files.
* [**sparta_ambiRoomSim**](../sparta-suite/#ambiroomsim) - A shoebox room simulator based on the image-source method, supporting multiple sources and ambisonic receivers.
* [**sparta_array2sh**](../sparta-suite/#array2sh) - A microphone array Ambisonics encoder (up to 10th order), with presets for several commercially available A-format and higher-order microphone arrays. The plug-in can also present objective evaluation metrics for the currently selected configuration.
* [**sparta_beamformer**](../sparta-suite/#beamformer) - A spherical harmonic domain beamforming plug-in with multiple beamforming strategies (up to 128 output beams).
* [**sparta_binauraliser**](../sparta-suite/#binauraliser) - A binaural panner (up to 128 input channels) with a built-in SOFA loader and head-tracking support via OSC messages.
* [**sparta_binauraliserNF**](../sparta-suite/#binauralisernf) - Binauraliser, with the addition of proximity filtering for near field sound sources.
* [**sparta_decorrelator**](../sparta-suite/#decorrelator) - A simple multi-channel signal decorrelator (up to 128 input channels).
* [**sparta_dirass**](../sparta-suite/#dirass) - A sound-field visualiser based on re-assigning the energy of beamformers. This re-assignment is based on DoA estimates extracted from "spatially-constrained" regions, which are centred around each beamformer look-direction.
* [**sparta_matrixconv**](../sparta-suite/#matrixconv) - A basic matrix convolver with an optional partitioned convolution mode. The user need only specify the number of inputs and load the filters via a wav file.
* [**sparta_multiconv**](../sparta-suite/#multiconv) - A basic multi-channel convolver with an optional partitioned convolution mode. Unlike "MatrixConv", this plug-in does not perform any matrixing. Instead, each input channel is convolved with the respective filter; i.e. numInputs = numFilters = numOutputs.
* [**sparta_6DoFconv**](../sparta-suite/#6dofconv) - A time-varying partitioned convolution multi-channel convolver for SOFA files containing RIRs with multiple listener positions.
* [**sparta_panner**](../sparta-suite/#panner) - A 3D loudspeaker array panner using the VBAP method (up to 128 inputs and outputs).
* [**sparta_pitchshifter**](../sparta-suite/#pitchshifter) - A simple multi-channel pitch shifter (up to 128 channels) based on the phase vocoder approach.
* [**sparta_powermap**](../sparta-suite/#powermap) - A sound-field visualisation plug-in based on ambisonic signals as input (up to 10th order), with PWD/MVDR/MUSIC/Min-Norm options.
* [**sparta_rotator**](../sparta-suite/#rotator) - A flexible ambisonic rotator (up to 10th order) with head-tracking support via OSC messages.
* [**sparta_sldoa**](../sparta-suite/#sldoa) - A frequency-dependent sound-field visualiser (up to 10th order), based on depicting the direction-of-arrival (DoA) estimates derived from spatially localised active-intensity vectors. The low frequency estimates are shown with blue icons, mid-frequencies with green, and high-frequencies with red.
* [**sparta_spreader**](../sparta-suite/#spreader) - An arbitrary array (e.g. HRIRs or microphone array IRs) panner with coherent and incoherent spreading options.

### COMPASS 

[COMPASS Suite →]({{< relref "compass-suite" >}})

* [**compass_binaural**](../compass-suite/#binaural) - An adaptive binaural ambisonic decoder (up to 3rd order input) based on the parametric COMPASS model, with a built-in SOFA loader and head-tracking support via OSC messages.
* [**compass_binauralVR**](../compass-suite/#binauralvr) - Same as the compass_binaural plugin, but also supporting listener translation around the receiver position and support for multiple simultaneous listeners.
* [**compass_decoder**](../compass-suite/#decoder) - A parametrically enhanced loudspeaker ambisonic decoder (up to 3rd order input).
* [**compass_6dof**](../compass-suite/#6dof) - A six degrees-of-freedom (6DoF) renderer based on multiple Ambisonic receivers as input, which supports listener translation both within and beyond the convex hull of the receiver arrangement.
* [**compass_gravitator**](../compass-suite/#gravitator) - A parametric sound-field focussing plug-in.
* [**compass_sidechain**](../compass-suite/#sidechain) - A plug-in that manipulates the spatial properties of one Ambisonic recording based on the spatial analysis of a different recording.
* [**compass_spatedit**](../compass-suite/#spatedit) - A flexible spatial editing plug-in.
* [**compass_tracker**](../compass-suite/#tracker) - A multiple target acoustic tracker which can optionally steer a beamformer towards each target.
* [**compass_upmixer**](../compass-suite/#upmixer) - An Ambisonic upmixer (1-3rd order input, 2-7th order output).

### HO-DirAC 

[HO-DirAC Suite →]({{< relref "hodirac-suite" >}})

* [**hodirac_binaural**](../hodirac-suite/#binaural) - An adaptive binaural ambisonic decoder (up to 3rd order input) based on the parametric HO-DirAC model, with a built-in SOFA loader and head-tracking support via OSC messages.
* [**hodirac_decoder**](../hodirac-suite/#decoder) - A parametrically enhanced loudspeaker ambisonic decoder (up to 3rd order input).
* [**hodirac_upmixer**](../hodirac-suite/#upmixer) - An Ambisonic upmixer (1-3rd order input, 2-7th order output).

Note these plug-ins are released under their own [licensing terms](../hodirac-suite/#license).

### Other plug-ins
* [**hades_renderer**](../hades/#plug-in-description) - A flexible head-worn microphone array to binaural renderer.
* [**cropac_binaural**](../cropac-binaural/#plug-in-description) - An adaptive binaural first-order ambisonic decoder based on the parametric CroPaC model, with a built-in SOFA loader and head-tracking support via OSC messages.
* [**HOSIRR**](../hosirr/#application-description) - An Ambisonic room impulse response (RIR) renderer for arbitrary loudspeaker setups, based on the Higher-order Spatial Impulse Response Rendering (HO-SIRR) algorithm.
* [**UltrasonicSuperHearing**](../ultrasonicsuperhearing/#UltrasonicSuperHearing) - A plug-in for the binaural reproduction of ultrasonic sound sources captured using a 6-sensor ultrasonic microphone array, which uses direction-of-arrival estimation and pitch-down-shifting prior to binauralisation in order to provide the appropriate localisation cues.