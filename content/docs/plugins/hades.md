---
title: "HADES"
description: "Plug-in description for the hades-renderer."
lead: "Plug-in description for the hades-renderer."
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 135
toc: true
---

## Paper abstract

In this article, the application of spatial covariance matching is investigated for the task of producing spatially enhanced binaural signals using head-worn microphone arrays. A two-step processing paradigm is followed, whereby an initial estimate of the binaural signals is first produced using one of three suggested binaural rendering approaches. The proposed spatial covariance matching enhancement is then applied to these estimated binaural signals, with the intention of producing refined binaural signals that more closely exhibit the correct spatial cues; as dictated by the employed sound-field model and associated spatial parameters.
It is demonstrated, through both objective and subjective evaluations, that the proposed enhancements in the majority of cases produce binaural signals which more closely resemble the spatial characteristics of simulated reference signals, when the enhancement is applied to, and compared against, the three suggested starting binaural rendering approaches. Furthermore, it is shown that the enhancement produces spatially similar output binaural signals when using these three different approaches; thus, indicating that the enhancement is general in nature, and could therefore be employed to enhance the outputs of other similar binaural rendering algorithms. 

## Plug-in description

<img src="HADES_Renderer_GUI.png" alt="" style="max-width: 95%"/></br>

An implementation of the general parametric binaural rendering framework described in [1], which primarily concerns head-worn microphone arrays such as: augmented reality (AR) headsets and binaural hearing aids. 

The plug-in works by first loading a dense grid of microphone array impulse response (IR) measurements via a SOFA file. Note that the measurement grid will dictate the localisation and spatialisation precision of the algorithms, for example: loading 360 IR, measured for every 1 degree on the horizontal plane, will mean that horizontal performance will be high, but elevated sources will not be localised or spatialised (at least, not particularly well); whereas, loading 1000+ IR measurements for a spherical t-design will obtain similar spatial resolution achieved by e.g. the COMPASS decoders, over the whole sphere. 

Once the microphone array IRs have been loaded, the implemented algorithms will binaurally reproduce the captured sound-field using a baseline method, such as: 1) simply taking two reference signals (one for each ear) and routing them to the binaural channels, 2) employing filter-and-sum (FaS) beamformers to better isolate the source signals based on direction-of-arrival estimates, or 3) using binaural minimum-variance distortionless response (BMVDR) beamformers instead. The binaural signals are then spatially enhanced via the spatial covariance matching solution described in [1], which relies on first specifying target inter-aural cues dictated by the assumed sound-field model and estimated spatial parameters. The spatial enhancement operation is then tasked with mixing the baseline binaural signals in an optimal and adaptive manner, such that the resultant binaural signals exhibit these target inter-aural cues; therefore, preserving the localisation cues of all sound sources in the scene, and the inter-aural coherence cues of diffuse reverberation. Note that, optionally, the default HRIRs (of a Kemar dummy head) may also be replaced by loading a SOFA file.

Since the method conducts a parameterisation of the input sound-field, the proposed method [1] can accommodate spatial audio effects and sound-field modifications through simple parameter manipulations; such as those described in [2]. In this plug-in, the direct-to-diffuse balance may be manipulated per frequency band, and the gain of directional components may be adjusted for different directions.

## About the developers
    
* **Leo McCormack**: a doctoral candidate at Aalto University.
* **Janani Fernandez**: a doctoral candidate at Aalto University.


## License

This plug-in may be used for academic, personal, and/or commercial use. The source code may also be used for commercial purposes, provided that the terms of the GPLv3 license are fulfilled. This requires that the original code and/or any derived works must also be open-sourced and made available under the same GPLv3 license, if it is to be used for commercial purposes.

## References

* [1] Fernandez, J., McCormack, L., Hyvärinen, P., Politis, A., Pulkki, V. (2022). "Enhancing binaural rendering of head-worn microphone arrays through the use of adaptive spatial covariance matching." Accepted for publication in The Journal of the Acoustical Society of America.
* [2] McCormack, L., Politis, A., and Pulkki, V., 2021, September. <a href="../../help/related-publications/#mccormack2021parametric"><b>Parametric Spatial Audio Effects Based on the Multi-Directional Decomposition of Ambisonic Sound Scenes. </b></a> <br> <i>in</i> Proceedings of the 24th International Conference on Digital Audio Effects (DAFx20in21), (pp. 214-221).