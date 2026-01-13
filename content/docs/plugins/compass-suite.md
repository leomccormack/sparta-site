---
title: "COMPASS"
description: "Plug-in descriptions for the COMPASS suite."
lead: ""
date: 2021-08-15T15:21:01+02:00
lastmod: 2021-08-15T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 130
toc: true
---

COMPASS is a collection of parametric spatial audio plug-ins. 

These plug-ins conform to the Ambisonic Channel Number (ACN) ordering convention and offer support for both orthonormalised (N3D) and semi-normalised (SN3D) normalisation schemes (note that the AmbiX format refers to the combination of ACN and SN3D). The maximum transform order for these plug-ins is 3rd.

{{< alert icon="👉" text="Hover your mouse cursor over plug-in parameters to reveal tooltips! :-)" />}}

## Plug-in descriptions 

Example REAPER projects can be found [**here**](https://github.com/leomccormack/sparta-reaper-examples).

### Decoder
<img src="Decoder_GUI.png" alt="" style="max-width: 85%"></br>

**Input**: Ambisonics | **Output**: Arbitrary loudspeaker array | [**Related publication**](../../help/related-publications/politis2018compass.pdf)
    
The plug-in offers the following functionality:
* User-specified loudspeaker angles up to 64 channels.
* Headphone binaural monitoring of the loudspeaker outputs, with support for user-provided personalised binaural filters (HRTFs) via the SOFA format. 
* Balance control between the extracted direct sound components and the ambient component, per frequency band. 
* Mixing control between fully parametric decoding and traditional linear Ambisonic decoding (EPAD), per frequency band. 
    
The "Diffuse-to-Direct" control allows the user to give more prominence to the direct sound components (an effect similar to subtle dereverberation), or to the ambient component (an effect similar to emphasising reverberation in the recording). When set in the middle, the two audio streams are balanced. 
    
The "Linear-to-Parametric" control allows the user to mix the output between standard linear Ambisonic decoding and the COMPASS parametric decoding. This control can be used in cases where parametric processing sounds too aggressive, or if the user prefers some degree of localisation blur offered by linear Ambisonic decoding.

The plug-in is considered by the authors a production tool and, due to its time-frequency processing, requires internal audio buffer sizes of 1024 samples. Hence we do not consider it as a low-latency plug-in and therefore it is not suitable for interactive input. For cases such as interactive binaural rendering for VR with head-tracking, please use the <b>COMPASS|Binaural</b> variant.

**Developers**: Leo McCormack and Archontis Politis.

### Binaural
<img src="Binaural_GUI.png" alt="" style="max-width: 85%"></br>

**Input**: Ambisonics | **Output**: Binaural | [**Related publication**](../../help/related-publications/mccormack2022estimating.pdf)
    
This is a binaural playback optimised version of the COMPASS decoder. It bypasses loudspeaker rendering and using binaural filters (HRTFs) directly, which can be user-provided and personalised with the SOFA format. For the plug-in parameters, see the description of the <b>Binaural|Decoder</b> above. Additionally the plug-in can receive OSC rotation angles from a headtracker at a user specified port, in the yaw-pitch-roll convention.

This version is intended mostly for head-tracked binaural playback of Ambisonic content at interactive update rates, usually in conjunction with a head-mounted display (HMD). The plug-in requires an audio buffer size of at least 512 samples (~10msec at 48kHz). The averaging parameters can be used to make the parametric analysis and synthesis more or less responsive.
    
**Developers**: Leo McCormack and Archontis Politis.
    
### BinauralVR
<img src="binauralVR_GUI.png" alt="" style="max-width: 95%"></br>

**Input**: Ambisonics | **Output**: (multi-)Binaural | [**Related publication**](../../help/related-publications/mccormack2021parametric.pdf)
    
Same as the COMPASS|Binaural plug-in, except also supporting listener translation away from the recording position. The user must first select the assumed distance of the sources. For simplicity, it is assumed that all sources are projected onto the surface of a sphere. 

The listener position and head orientation can be passed via an OSC message: \xyzypr[6], where x,y,z are in metres, and y,p,r are the yaw-pitch-roll angles in degrees (right-hand-rule).
    
**Developers**: Leo McCormack and Archontis Politis.

### 6DoF
<img src="COMPASS_6DoF_GUI.png" alt="" style="max-width: 100%"></br>

**Input**: multi-Ambisonics | **Output**: Binaural/Ambisonics/Objects | [**Related publication**](../../help/related-publications/mccormack2022object.pdf) | [**REAPER example**](https://zenodo.org/record/5767394)

A six degrees-of-freedom (6DoF) renderer based on multiple Ambisonic receivers as input. The source positions may either be specified or tracked similarly as described in [[12]](../../help/related-publications/mccormack2021real.pdf). The plug-in may be configured to either output the isolated source object signals (one per track), or to spatialise the sound scene (including reverberation) from the perspective of the listener position/orientation over headphones or as Ambisonics output. If targetting Ambisonics, any Ambisonic decoder may then be used to auralise the translated sound scene.

Note that all receiver channels must be stacked on-top of eachother, for example: 3 first-order receivers should be assigned to input channels 1-4, 5-8, 9-12, respectively. Therefore, due to the 64-channel VST2 limitation, the plug-in supports either: 16x first-order, 7x second-order, 4x third-order receivers etc.
    
**Developers**: Leo McCormack and Archontis Politis.
    
### Tracker
<img src="tracker_GUI.png" alt="" style="max-width: 98%"></br>

**Input**: Ambisonics | **Output**: Objects/Binaural | [**Related publication**](../../help/related-publications/mccormack2021real.pdf)

The Tracker plug-in employs a multi-source tracker [11,12] to cluster and associate estimated directions with distinct sound objects/targets. 
    
Optionally, a beamformer can be steered to each target direction and outputted as individual signals (one target signal per output channel - akin to decomposing the scene into its individual "stems"), or as a binauralisation of these individual "stems" (spatialised in their respective target directions).
    
Note that multi-source tracking has been an active research topic for several decades, but it is still considered a difficult task. While we are confident in the robustness of this tracker and its implementation, there is still a learning curve to effectively tune the parameters for a specific sound scene/distribution. If the sound scene is very noisy or complex and encoded with first-order/lower resolution, then robust tracking may not be possible. A general starting point is to first disable "Plot Targets" and tune the "Analysis Settings" until the direction estimates (plotted in the colour red) look reasonably clean. If you can make out the trajectories of the sources, then re-enable "Plot Targets" and try a few of the "Tracker Settings" presets and tune things from there. Note that each tracker parameter also has a tooltip describing how it influences the tracking.
    
### Upmixer
<img src="upmixer_GUI.png" alt="" style="max-width: 80%"></br>

**Input**: Ambisonics | **Output**: (higher-order) Ambisonics

This plug-in employs COMPASS for the task of upmixing a lower-order Ambisonic recording to a higher-order Ambisonic recording. It is intended for users that are already working with a preferred linear Ambisonic decoding workflow of higher-order Ambisonic content, and wish to combine lower-order Ambisonic material with increased spatial resolution. One can upmix first, second, or third-order material (4,9,16 channels) to up-to seventh-order material (64 channels).

**Developers**: Leo McCormack and Archontis Politis.
    
### SideChain
<img src="sidechain_GUI.png" alt="" style="max-width: 60%"></br>

**Input**: 2xAmbisonics | **Output**: Ambisonics | [**Related publication**](../../help/related-publications/mccormack2021parametric.pdf)

This plug-in applies the COMPASS analysis on one sound scene (scene A [channels 1-16] or scene B [channels 17-32]), and uses the estimated spatial parameters to manipulate the signals of the second sound scene. If scene A and B are the same, then the plug-in becomes functionally identical to the COMPASS|Upmixer.
    
### SpatEdit
<img src="spatEdit_A.png" alt="" style="max-width: 90%"></br>

**Input**: Ambisonics | **Output**: Ambisonics | [**Related publication**](../../help/related-publications/mccormack2021parametric.pdf)

The SpatEdit plug-in is intended to be used with two instances. The first instance of the plug-in allows the user to place markers on an equirectangular representation of the sphere. Alternatively the markers can automatically follow the directions of sound sources through use of the tracker. The source beamformer signals are then outputted by the first instance of the plug-in (A), where the user can then apply any conventional single-channel audio effect, re-balance their levels, or re-order the signals. These manipulated beamformer signals are then passed to the second instance of the plug-in (B), which also receives the residual signals from the first plug-in instance in the background, and the COMPASS synthesis is conducted to obtain the output Ambisonic signals. Alternatively, the residual stream signals may be outputted by the first plug-in instance instead (and the beamformer signals passed internally to the second plug-in instance), which instead allows conventional linear  Ambisonics transformations to be applied to only the ambient parts of the scene.
  
**Developers**: Leo McCormack and Archontis Politis.
    
### Gravitator
<img src="GravitatorGUI_alpha6_src%2076%200%20%20-24%2045%20-80%20-30.png" alt="" style="max-width: 90%"></br>

**Input**: Ambisonics | **Output**: Ambisonics | [**Related publication**](../../help/related-publications/mccormack2021parametric.pdf)

A spatial "warping" effect that pulls directional components of the sound scene towards user defined markers, with a certain degree of "gravitational-pull". The Ambient components of the sound scene will remain unchanged.
  
**Developers**: Leo McCormack and Archontis Politis.


## The COMPASS framework

COMPASS is a framework for parametric spatial audio processing of sound scenes captured in the Ambisonics format. Parametric methods, such as Directional Audio Coding (DirAC) and HARPEX, have gained notoriety in recent years for being able to achieve sharpness or envelopment beyond first or lower-order traditional Ambisonics playback, using the same lower-order Ambisonics signals. Contrary to the time-invariant linear processing of Ambisonics, which does not consider the sound components that comprise the sound scene, parametric methods assume a sound-field model for the sound scene and estimate the model parameters in the Ambisonics recording, over both time and frequency. The parameters are then used to render or upmix the sound scene flexibly to any playback system, without the constraints of traditional signal-independent Ambisonic decoders. Furthermore, the spatial parameters allow flexible manipulation of the sound scene content in ways that are not possible with traditional Ambisonics processing.

The COMPASS framework has been developed by Dr. Archontis Politis with contributions from Dr. Sakari Tervo and Dr. Leo McCormack, and published in <a href="../../help/related-publications/politis2018compass.pdf">[1]</a>. The method adopts a general sound-field model, estimating multiple direct sound components in every time-frequency block, and an ambient component capturing reverberation and other diffuse sounds. Here is a table of the COMPASS model compared to other published parametric techniques (note that M refers to the number of channels):  

<img src="parametric_ambisonic_models.png" alt="" style="max-width: 95%"></br>
    
In COMPASS, the ambient component is also spatial and can have directionality, contrary to previous models that force it to be isotropic. The audio plug-ins apply this framework to different spatial audio production tasks. Note that the plug-ins are part of an active research project and we therefore expect to keep improving them in the future. However, we believe that they can already prove useful to users and creators.
     
## About the developers
    
* **Leo McCormack**: former postdoctoral researcher at Aalto University.
* **Archontis Politis** professor at Tampere University.

## License

All of the plug-ins in the COMPASS suite may be used for academic, personal, and/or commercial use.

## References

[1] Politis, A., Tervo S., and Pulkki, V. (2018) <a href="../../help/related-publications/politis2018compass.pdf"><b>COMPASS: Coding and Multidirectional Parameterization of Ambisonic Sound Scenes.</b></a> <br> IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP).
    
[2] Pulkki, V. (2007) <b>Spatial sound reproduction with directional audio coding.</b> <br> Journal of the Audio Engineering Society 55.6: 503-516.
    
[3] Pulkki, V., Politis, A., Laitinen, M.-V., Vilkamo, J., Ahonen, J. (2017). <b>First-order directional audio coding (DirAC).</b> <br> <i>in</i> Parametric Time-Frequency Domain Spatial Audio, Wiley, p.89-138.
    
[4] Berge, S. and Barrett, N. (2010). <b>High angular resolution planewave expansion.</b> <br> 2nd International Symposium on Ambisonics and Spherical Acoustics.
    
[5] Politis, A., Vilkamo, J., and Pulkki, V. (2015). <a href="../../help/related-publications/politis2015sector.pdf"> <b>Sector-based parametric sound field reproduction in the spherical harmonic domain.</b></a> <br> IEEE Journal of Selected Topics in Signal Processing, 9(5), 852-866.

[6] Politis, A., McCormack, L., and Pulkki, V. (2017, October). <a href="../../help/related-publications/politis2017enhancement.pdf"> <b>Enhancement of ambisonic binaural reproduction using directional audio coding with optimal adaptive mixing</b></a>.</b> <br> In 2017 IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA) (pp. 379-383). IEEE.

[7] Politis, A. and Pulkki, V. (2017). <b>Higher-Order Directional Audio Coding.</b> <br><i>in</i> Parametric Time-Frequency Domain Spatial Audio, Wiley, p.141.

[8] Wabnitz, A., Epain, N., McEwan, A., Jin, C. (2011). <b>Upscaling ambisonic sound scenes using compressed sensing techniques.</b> <br> IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA).

[9] Kolundzija, M., and Faller, C. (2018). <b>Advanced B-Format Analysis.</b><br> Audio Engineering Society Convention 144.
    
[10] Sch&ouml;rkhuber, C., and H&ouml;ldrich, R. (2019, March). <b>Linearly and Quadratically Constrained Least-Squares Decoder for Signal-Dependent Binaural Rendering of Ambisonic Signals.</b> <br> In Audio Engineering Society Conference: 2019 AES International Conference on Immersive and Interactive Audio. Audio Engineering Society.
    
[11] S&auml;rkk&auml;, S., Vehtari, A. and Lampinen, J., 2004, June. <b>Rao-Blackwellized Monte Carlo data association for multiple target tracking. </b> <br> <i>in</i> Proceedings of the seventh international conference on information fusion (Vol. 1, pp. 583-590). I.

[12] McCormack, L., Politis, A., S&auml;rkk&auml;, S., and Pulkki, V., 2021. <a href="../../help/related-publications/mccormack2021real.pdf"><b>Real-Time Tracking of Multiple Acoustical Sources Utilising Rao-Blackwellised Particle Filtering. </b></a> <br> <i>in</i> 29th European Signal Processing Conference, EUSIPCO 2021, (pp. 206-210).

[13] McCormack, L., Politis, A., and Pulkki, V., 2021, September. <a href="../../help/related-publications/mccormack2021parametric.pdf"><b>Parametric Spatial Audio Effects Based on the Multi-Directional Decomposition of Ambisonic Sound Scenes. </b></a> <br> <i>in</i> Proceedings of the 24th International Conference on Digital Audio Effects (DAFx20in21), (pp. 214-221).
