---
title: "Overview of the plug-ins"
description: "What's included in the SPARTA installer?"
lead: "SPARTA is a collection of flexible VST audio plug-ins for spatial audio production, reproduction and visualisation, developed primarily by members of the Acoustics Lab at Aalto University, Finland."
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
These plug-ins employ parametric processing and are signal-dependent. They aim to go beyond conventional linear Ambisonics algorithms, used by the baseline SPARTA plug-ins, by extracting meaningful parameters over time and subsequently employing them to map the input to the output in a more informed manner.

## All included plug-ins

### SPARTA plug-ins

More detailed descriptions can be found in [SPARTA Suite →]({{< relref "sparta-suite" >}})

* [**sparta_ambiBIN**](../sparta-suite/#ambibin) - A binaural ambisonic decoder (up to 7th order) with a built-in SOFA loader and head-tracking support via OSC messages. Includes: Least-Squares (LS), spatial re-sampling (SPR), time-alignment (TA), and magnitude least-squares (Mag-LS) decoding options.
* [**sparta_ambiDEC**](../sparta-suite/#ambidec) - A frequency-dependent loudspeaker ambisonic decoder (up to 7th order) with user specifiable loudspeaker directions (up to 64), which may be optionally imported via JSON configuration files. Includes: All-Round (AllRAD), Energy-Preserving (EPAD), Spatial (SAD), and Mode-Matching (MMD) ambisonic decoding options. The loudspeaker signals may also be binauralised for headphone playback.
* [**sparta_ambiDRC**](../sparta-suite/#ambidrc) - A frequency-dependent dynamic range compressor for ambisonic signals (up to 7th order).
* [**sparta_ambiENC**](../sparta-suite/#ambienc) - An ambisonic encoder/panner (up to 7th order), with support for up to 64 input channels; the directions for which may also be imported via JSON configuration files.
* [**sparta_ambiRoomSim**](../sparta-suite/#ambiroomsim) - A shoebox room simulator based on the image-source method, supporting multiple sources and ambisonic receivers..
* [**sparta_array2sh**](../sparta-suite/#array2sh) - A microphone array spatial encoder (up to 7th order), with presets for several commercially available A-format and higher-order microphone arrays. The plug-in can also present objective evaluation metrics for the currently selected configuration.
* [**sparta_beamformer**](../sparta-suite/#beamformer) - A spherical harmonic domain beamforming plug-in with multiple beamforming strategies (up to 64 output beams).
* [**sparta_binauraliser**](../sparta-suite/#binauraliser) - A binaural panner (up to 64 input channels) with a built-in SOFA loader and head-tracking support via OSC messages.
* [**sparta_decorrelator**](../sparta-suite/#decorrelator) - A simple multi-channel signal decorrelator (up to 64 input channels).
* [**sparta_dirass**](../sparta-suite/#dirass) - A sound-field visualiser based on re-assigning the energy of beamformers. This re-assigment is based on DoA estimates extracted from "spatially-constrained" regions, which are centred around each beamformer look-direction.
* [**sparta_matrixconv**](../sparta-suite/#matrixconv) - A basic matrix convolver with an optional partitioned convolution mode. The user need only specify the number of inputs and load the filters via a wav file.
* [**sparta_multiconv**](../sparta-suite/#multiconv) - A basic multi-channel convolver with an optional partitioned convolution mode. Unlike "MatrixConv", this plug-in does not perform any matrixing. Instead, each input channel is convolved with the respective filter; i.e. numInputs = numFilters = numOutputs.
* [**sparta_panner**](../sparta-suite/#panner) - A frequency-dependent 3-D panner using the VBAP method (up to 64 inputs and outputs).
* [**sparta_powermap**](../sparta-suite/#powermap) - A sound-field visualisation plug-in based on ambisonic signals as input (up to 7th order), with PWD/MVDR/MUSIC/Min-Norm options.
* [**sparta_rotator**](../sparta-suite/#rotator) - A flexible ambisonic rotator (up to 7th order) with head-tracking support via OSC messages.
* [**sparta_sldoa**](../sparta-suite/#sldoa) - A frequency-dependent sound-field visualiser (up to 7th order), based on depicting the direction-of-arrival (DoA) estimates derived from spatially localised active-intensity vectors. The low frequency estimates are shown with blue icons, mid-frequencies with green, and high-frequencies with red.
* [**sparta_spreader**](../sparta-suite/#spreader) - An arbitrary array (e.g. HRIRs or microphone array IRs) panner with coherent and incoherent spreading options.

### COMPASS plug-ins
{{< alert icon="👉" text="These plug-ins are intended for experienced users." />}}
More detailed descriptions can be found in [COMPASS Suite →]({{< relref "compass-suite" >}})

* **compass_binaural** - A binaural ambisonic decoder (up to 3rd order input) based on the parametric COMPASS model, with a built-in SOFA loader and head-tracking support via OSC messages.
* **compass_binauralVR** - Same as the compass_binaural plugin, but also supporting listener translation around the receiver position and support for multiple simultaneous listeners.
* **compass_decoder** - A parametrically enhanced loudspeaker ambisonic decoder (up to 3rd order input).
* **compass_gravitator** - A parametric sound-field focussing plug-in.
* **compass_sidechain** - A plug-in that manipulates the spatial properties of one Ambisonic recording based on the spatial analysis of a different recording.
* **compass_spatedit** - A flexible spatial editing plug-in.
* **compass_tracker** - A multiple target acoustic tracker which can optionally steer a beamformer towards each target.
* **compass_upmixer** - An Ambisonic upmixer (1-3rd order input, 2-7th order output).

### HO-DirAC plug-ins
{{< alert icon="👉" text="These plug-ins are intended for experienced users." />}}
More detailed descriptions can be found in [HO-DirAC Suite →]({{< relref "hodirac-suite" >}})

* **hodirac_binaural** - A binaural ambisonic decoder (up to 3rd order input) based on the parametric HO-DirAC model, with a built-in SOFA loader and head-tracking support via OSC messages.
* **hodirac_decoder** - A parametrically enhanced loudspeaker ambisonic decoder (up to 3rd order input).
* **hodirac_upmixer** - An Ambisonic upmixer (1-3rd order input, 2-7th order output).

### Other plug-ins
* **cropac_binaural** - A binaural 1st order ambisonic decoder based on the parametric CroPaC model, with a built-in SOFA loader and head-tracking support via OSC messages.
* **HOSIRR** - An Ambisonic room impulse response (RIR) renderer for arbitrary loudspeaker setups, based on the Higher-order Spatial Impulse Response Rendering (HO-SIRR) algorithm; more information can be found here.