---
title: "COMPASS"
description: "Plug-in descriptions for the COMPASS suite."
lead: "Plug-in descriptions for the COMPASS suite."
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

## Plug-in descriptions 

COMPASS is a collection of flexible VST/LV2 audio plug-ins for spatial audio production, manipulation, and reproduction, developed by Dr. Archontis Politis, Dr. Leo McCormack and Dr. Sakari Tervo at the Acoustics Lab, Aalto University. 

COMPASS is a framework for parametric spatial audio processing of sound scenes captured in the Ambisonics format. Parametric methods, such as Directional Audio Coding (DirAC) and HARPEX, have gained notoriety recently for being able to achieve sharpness or envelopment beyond first or lower-order traditional Ambisonics playback, using the same lower-order Ambisonics signals. Contrary to the time-invariant linear processing of Ambisonics, which does not consider the sound components that comprise the sound scene, parametric methods assume a sound-field model for the sound scene and track the model parameters in the Ambisonics recording, in both time and frequency. The parameters are then used to render or upmix the sound scene flexibly to any playback system, without the constraints of lower-order Ambisonics. Furthermore, the spatial parameters allow flexible manipulation of the sound scene content in ways that are not possible with traditional Ambisonics processing.

The COMPASS framework has been developed by Dr. Archontis Politis with contributions from Dr. Sakari Tervo and Dr. Leo McCormack, and published in <a href="../../help/related-publications/politis2018compass.pdf">[1]</a>. The method is quite general in its model and estimates multiple direct sound components in every time-frequency block, and an ambient component capturing reverberation and other diffuse sounds. Here is a table of the COMPASS model compared to other published parametric techniques (note that M refers to the number of channels):  

<img src="parametric_ambisonic_models.png" alt="" style="max-width: 95%"></br>
    
In COMPASS, the ambient component is also spatial and can have directionality, contrary to previous models that force it to be isotropic. The VST/LV2 plugins apply this framework to different spatial audio production tasks. Note that the plugins are still a work in progress and we expect to keep improving them in the future, however, we believe that they can already prove useful to users and creators.

### Decoder
<img src="Decoder_GUI.png" alt="" style="max-width: 85%"></br>
    
The COMPASS decoder is a parametric decoder for first, second, and third-order Ambisonics to arbitrary loudspeaker setups. The plugin offers the following functionality:
* User-specified loudspeaker angles for up to 64 channels, or alternatively, presets for popular 2D and 3D set-ups. 
* Headphone binaural monitoring of the loudspeaker outputs, with support for user-provided personalised binaural filters (HRTFs) in the SOFA format. 
* Balance control between the extracted direct sound components and the ambient component, in frequency bands. 
* Mixing control between fully parametric decoding and linear Ambisonic decoding, in frequency bands. 
    
The "Diffuse-to-Direct" control allows the user to give more prominence to the direct sound components (an effect similar to subtle dereverberation), or to the ambient component (an effect similar to emphasising reverberation in the recording). When set in the middle, the two are balanced. Note that the parametric processing can be quite aggressive, and if one pushes it to fully direct rendering in a complex multi-source sound scene with FOA signals only, artefacts can easily appear. However, with more balanced settings, such artefacts  should become imperceptible.
    
The "Linear-to-Parametric" control allows the user to mix the output between standard linear Ambisonic decoding and the COMPASS parametric decoding. This control can be used in cases where parametric processing sounds too aggressive, or if the user prefers some degree of increased localisation blur, offered by linear Ambisonic decoding.
    
The plugin is considered by the authors a production tool and, due to its time-frequency processing, requires audio buffer sizes of at least 1024 samples. Hence we do not consider it as a low-latency plugin and therefore it is not suitable for interactive input. For cases such as interactive binaural rendering for VR with head-tracking, see the <b>COMPASS|Binaural</b> variant.

A video demonstrating the functionality of the plug-in can be viewed here:

<iframe src="https://player.vimeo.com/video/312282907" width="600px" height="300px" style="max-width: 100%" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

This plug-in was developed by Leo McCormack and Archontis Politis.

### Binaural
<img src="Binaural_GUI.png" alt="" style="max-width: 85%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/politis2018compass.pdf), and includes the different ambience rendering options described in [**this publication**](../../help/related-publications/mccormack2022estimating.pdf).
    
This is an optimised version of the COMPASS decoder for binaural playback, bypassing loudspeaker rendering and using binaural filters (HRTFs) directly, which can be user-provided and personalised with the SOFA format. For the plugin parameters, see the description of the <b>Binaural|Decoder</b> above. Additionally the plugin can receive OSC rotation angles from a headtracker at a user specified port, in the yaw-pitch-roll convention.

This version is intended mostly for head-tracked binaural playback of Ambisonic content at interactive update rates, usually in conjunction with a head-mounted display (HMD). The plugin requires an audio buffer size of at least 512 samples (~10msec at 48kHz). The averaging parameters can be used to make the parametric analysis and synthesis more or less responsive, providing the user with a means to adjust them optimally for a particular sound scene.
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### BinauralVR
<img src="binauralVR_GUI.png" alt="" style="max-width: 95%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2021parametric.pdf).
    
Same as the COMPASS|Binaural plug-in, except it also supports listener translation around the receiver position. The user must first select the assumed distance of the sources. For simplicity, it is assumed that all sources are projected onto the surface of a sphere. The plug-in may then be informed of the listener position and orientation, either via its user interface sliders, or by sending  the Cartesian coordinates and rotation angles outputted by an external tracking device; such as a virtual or augmented reality headset.
    
The listener position and head orientation can be passed via an OSC message: \xyzypr[6], where x,y,z are in metres, and y,p,r are the yaw-pitch-roll angles in degrees (right-hand-rule).
    
This plug-in was developed by Leo McCormack and Archontis Politis.

### 6DoF
<img src="COMPASS_6DoF_GUI.png" alt="" style="max-width: 100%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2022object.pdf), and an example REAPER project based on the scenario described in the publication can be [**found here**](https://zenodo.org/record/5767394).

A parametric six degrees-of-freedom (6DoF) renderer based on multiple Ambisonic receivers as input, which supports listener translation both within and beyond the convex hull of the receiver arrangement. The source positions may either be specified or tracked similarly as described in [[12]](../../help/related-publications/mccormack2021real.pdf). The plug-in may be configured to either output only the isolated source object signals (one per track), or to spatialise the sound scene (including reverberation) from the perspective of the listener position/orientation over headphones or as Ambisonics output. If targetting Ambisonics, any Ambisonic decoder may then be used to auralise the translated sound scene.

Note that all receiver channels must be stacked on-top of eachother, for example: 3 first-order receivers should be assigned to input channels 1-4, 5-8, 9-12, respectively. Therefore, due to the 64-channel VST2 limitation, the plug-in supports either: 16x first-order, 7x second-order, 4x third-order receivers etc.
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### Tracker
<img src="tracker_GUI.png" alt="" style="max-width: 98%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2021real.pdf).

The Tracker plug-in builds on the spatial analysis conducted by the COMPASS framework, but instead of using the information for synthesising loudspeaker or binaural signals, a multi-source tracker is employed to associate the estimated directions with their corresponding sources/targets. Therefore, this plugin can be used to visualise the trajectory of multiple sound sources present in an Ambisonic sound scene.
    
Optionally, a beamformer may then be steered to each target direction and outputted either as individual signals (one target signal per output channel; akin to decomposing the scene into its individual "stems"), or as a binauralisation of these individual "stems" (spatialised in their respective target directions).
    
Note that multi-source tracking has been an active research topic for several decades, but it is still considered to be a very difficult task. While we are confident in the robustness of this tracker and its implementation, there is still a learning curve to effectively tune the parameters for a specific sound scene/distribution. If the sound scene is very noisy or complex and encoded with first-order/lower resolution, then robust tracking may not even be possible. A general starting point is to first disable "Plot Targets" and tune the "Analysis Settings" until the direction estimates (plotted in the colour red) look reasonably clean. If you can make out the trajectories of the sources, then re-enable "Plot Targets" and try a few of the "Tracker Settings" presets and tune things from there. Note that each tracker parameter also has a tooltip describing how it influences the tracking, and the more these parameters/priors match the direction estimates distribution, the better the tracking will be.
    
The tracker implementation builds on the Rao-Blackwelized Monte Carlo Data Association (RBMCDA) framework [11,12]. It should be noted that Sequential Monte Carlo (SMC) methods (also referred to as particle-filtering methods) involve making hundreds/thousands of hypotheses, which are then selected randomly based on their predicted likelihoods. Therefore, every time the tracker is run it will give you a different "answer" for the same input scene, but if the tracker is tuned well then the result should be substantially similar each time. 
    
### Upmixer
<img src="upmixer_GUI.png" alt="" style="max-width: 80%"></br>

This plug-in employs COMPASS for the task of upmixing a lower-order Ambisonic recording to a higher-order Ambisonic recording. It is intended for users that are already working with a preferred linear Ambisonic decoding workflow of higher-order Ambisonic content, and wish to combine lower-order Ambisonic material with increased spatial resolution. One can upmix first, second, or third-order material (4,9,16 channels) to up-to seventh-order material (64 channels).
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### SideChain
<img src="sidechain_GUI.png" alt="" style="max-width: 60%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2021parametric.pdf).

This plug-in applies the COMPASS analysis on one sound scene (either scene A [channels 1-16] and scene B [channels 17-32]), and uses the estimated spatial parameters to manipulate the signals of the second sound scene. If scene A and B are the same, then the plugin is functionally identical to compass_upmixer.
    
### SpatEdit
<img src="spatEdit_A.png" alt="" style="max-width: 90%">
<img src="spatEdit_B.png" alt="" style="max-width: 90%"></br>
</br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2021parametric.pdf).

The SpatEdit plug-in is intended to be used with two instances. The first instance of the plug-in allows the user to place markers on an equirectangular representation of the sphere. Alternatively the markers can automatically follow the directions of sound sources through use of the tracker. The source beamformer signals are then outputted by the first instance of the plug-in (A), where the user can then apply any conventional single-channel audio effect, re-balance their levels, or re-order the signals. These manipulated beamformer signals are then passed to the second instance of the plug-in (B), which also receives the residual signals from the first plug-in instance internally, and the COMPASS synthesis is conducted to obtain the output SH signals. Alternatively, the residual stream signals may be outputted by the first plug-in instance instead (and the beamformer signals passed internally to the second plug-in instance), which instead allows conventional linear  Ambisonics transformations to be applied to only the ambient parts of the scene.
  
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### Gravitator
<img src="GravitatorGUI_alpha6_src%2076%200%20%20-24%2045%20-80%20-30.png" alt="" style="max-width: 90%"></br>

This plug-in is related to [**this publication**](../../help/related-publications/mccormack2021parametric.pdf).

A spatial "focussor" which pulls only the directional components of the sound scene towards user defined markers, with a certain degree of "gravitational-pull". The Ambient components of the sound scene remain unaltered.
  
This plug-in was developed by Leo McCormack and Archontis Politis.
     
## About the developers
    
* **Leo McCormack**: a postdoctoral researcher at Aalto University.  
* **Archontis Politis** a professor at Tampere University, specialising in spatial sound recording and reproduction, acoustic scene analysis and microphone array processing.  

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
