---
title: "COMPASS suite"
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

COMPASS VSTs is a collection of flexible VST audio plug-ins for spatial audio production, manipulation, and reproduction, developed by Dr. Archontis Politis, Leo McCormack and Dr. Sakari Tervo in the Acoustics Lab at Aalto University. 

COMPASS is a framework for parametric spatial audio processing of sound scenes captured in the Ambisonics format. Parametric methods, such as Directional Audio Coding (DirAC) or HARPEX have gained notoriety recently for being able to achieve sharpness or envelopment beyond first or lower-order traditional Ambisonics playback, using the same lower-order Ambisonics signals. Contrary to the time-invariant linear processing of Ambisonics, which does not consider the sound components that comprise the sound scene, parametric methods assume a sound-field model for the sound scene and track the model parameters in the Ambisonics recording, in both time and frequency. The parameters are then used to render or upmix the sound scene flexibly to any playback system, without the constraints of lower-order Ambisonics. Furthermore, the spatial parameters allow flexible manipulation of the sound scene content in ways that are not possible with traditional Ambisonics processing.

The COMPASS framework has been developed by Dr. Archontis Politis with contributions from Dr. Sakari Tervo and Leo McCormack, and published in <a href="#ref_compass">[1]</a>. The method is quite general in its model and estimates multiple direct sound components in every time-frequency block, and an ambient component capturing reverberation and other diffuse sounds. Here is a table of the COMPASS model compared to other published parametric techniques (note that M is the number of channels):  

<img src="parametric_ambisonic_models.png" alt="" width="700"></br>
    
In COMPASS, the ambient component is also spatial and can have directionality, contrary to previous models that force it to be isotropic. The VST plugins apply this framework to different spatial audio production tasks. Note that the plugins are still work in progress and we expect to keep improving them in the future, however, we believe that they can already prove useful to users and creators.

### Decoder
<img src="Decoder_GUI.png" alt="" width="600;"></br>
    
The COMPASS decoder is a parametric decoder for first, second, and third-order Ambisonics to arbitrary loudspeaker setups. The plugin offers the following functionality:
* User-specified loudspeaker angles for up to 64 channels, or alternatively, presets for popular 2D and 3D set-ups. 
* Headphone binaural monitoring of the loudspeaker outputs, with support for user-provided personalised binaural filters (HRTFs) in the SOFA format. 
* Balance control between the extracted direct sound components and the ambient component, in frequency bands. 
* Mixing control between fully parametric decoding and linear Ambisonic decoding, in frequency bands. 
    
The "Diffuse-to-Direct" control allows the user to give more prominence to the direct sound components (an effect similar to subtle dereverberation), or to the ambient component (an effect similar to emphasising reverberation in the recording). When set in the middle, the two are balanced. Note that the parametric processing can be quite aggressive, and if one pushes it to fully direct rendering in a complex multi-source sound scene with FOA signals only, artefacts can easily appear. However, with more balanced settings, such artefacts  should become imperceptible.
    
The "Linear-to-Parametric" control allows the user to mix the output between standard linear Ambisonic decoding and the COMPASS parametric decoding. This control can be used in cases where parametric processing sounds too aggressive, or if the user prefers some degree of increased localisation blur, offered by linear Ambisonic decoding.
    
The plugin is considered by the authors a production tool and, due to its time-frequency processing, requires audio buffer sizes of at least 1024 samples. Hence we do not consider it as a low-latency plugin and therefore it is not suitable for interactive input. For cases such as interactive binaural rendering for VR with head-tracking, see the <b>COMPASS|Binaural</b> variant.

A video showing the plugin in action and demonstrating its functionality can be found here:

<iframe src="https://player.vimeo.com/video/312282907" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

This plug-in was developed by Leo McCormack and Archontis Politis.

### Binaural
<img src="Binaural_GUI.png" alt="" width="600;"></br>
    
This is an optimised version of the COMPASS decoder for binaural playback, bypassing loudspeaker rendering and using binaural filters (HRTFs) directly, which can be user-provided and personalised with the SOFA format. For the plugin parameters, see the description of the <b>Binaural|Decoder</b> above. Additionally the plugin can receive OSC rotation angles from a headtracker at a user specified port, in the yaw-pitch-roll convention.

This version is intended mostly for head-tracked binaural playback of Ambisonic content at interactive update rates, usually in conjunction with a head-mounted display (HMD). The plugin requires an audio buffer size of at least 512 samples (~10msec at 48kHz). The averaging parameters can be used to make the parametric analysis and synthesis more or less responsive, providing the user with a means to adjust them optimally for a particular sound scene.
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### BinauralVR
<img src="binauralVR_GUI.png" alt="" width="700;"></br>
    
Same as the COMPASS|Binaural plug-in, except it also supports listener translation around the receiver position. The user must first select the assumed distance of the sources. For simplicity, it is assumed that all sources are projected onto the surface of a sphere. The plug-in may then be informed of the listener position and orientation, either via its user interface sliders, or by sending  the Cartesian coordinates and rotation angles outputted by an external tracking device; such as a virtual or augmented reality headset.
    
The listener position and head orientation can be passed via an OSC message: \xyzypr[6], where x,y,z are in metres, and y,p,r are the yaw-pitch-roll angles in degrees (right-hand-rule).
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### Tracker
<img src="tracker_GUI.png" alt="" width="720;"></br>

This VST builds on the spatial analysis conducted by the Coding and Multidirectional Parameterisation of Ambisonic Sound Scenes (COMPASS) framework, but instead of using the information for synthesising loudspeaker or binaural signals, a multi-source tracker is employed to associate the estimated directions with their corresponding sources/targets. Therefore, this VST can be used to visualise the trajectory of sound sources present in an Ambisonic sound scene.
    
Optionally, a beamformer may then be steered to each target direction and outputted either as individual signals (one target signal per output channel; akin to decomposing the scene into its individual "stems"), or as a binauralisation of these individual "stems" (spatialised in their respective target directions).
    
Note that multi-source tracking has been an active research topic for several decades, but it is still considered to be a very difficult task. While we are confident in the robustness of this tracker and its implementation, there is a quite large learning curve in order to effectively tune the parameters for a specific sound scene/distribution. If the sound scene is very noisy or complex and encoded with first-order/lower resolution, then robust tracking may not even be possible. A general starting point is to first disable "Plot Targets" and tune the "Analysis Settings" until the direction estimates (plotted in the colour red) look reasonably clean. If you can make out the trajectories of the sources, then re-enable "Plot Targets" and try a few of the "Tracker Settings" presets and tune things from there. Note that each tracker parameter also has a tooltip describing how it influences the tracking, and the more these parameters/priors match the direction estimates distribution, the better the tracking will be.
    
The tracker implementation builds on the Rao-Blackwelized Monte Carlo Data Association (RBMCDA) framework [11]. It should be noted that Sequential Monte Carlo (SMC) methods (also referred to as particle-filtering methods) involve making hundreds/thousands of hypotheses, which are then selected randomly based on their predicted likelihoods. Therefore, every time the tracker is run it will give you a different "answer" for the same input scene, but if the tracker is tuned well then the result should be substantially similar each time. 
    
This plug-in was developed by Leo McCormack.
    
### Upmixer
<img src="upmixer_GUI.png" alt="" width="530;"></br>

This VST employs COMPASS for the task of upmixing a lower-order Ambisonic recording to a higher-order Ambisonic recording. It is intended for users that are already working with a preferred linear Ambisonic decoding workflow of higher-order Ambisonic content, and wish to combine lower-order Ambisonic material with increased spatial resolution. One can upmix first, second, or third-order material (4,9,16 channels) to up-to seventh-order material (64 channels).
    
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### SideChain
<img src="sidechain_GUI.png" alt="" width="400;"></br>

This VST is a bit of an experiment. Applying the COMPASS analysis to two different sound scenes (scene A [channels 1-16] and scene B [channels 17-32]), and using the estimated spatial parameters from one scene to manipulate the signals of the other scene.
    
Note that, if scene A and B are the same, then the plugin is functionally identical to compass_upmixer.
    
This plug-in was developed by Leo McCormack.
    
### SpatEdit
<img src="spatEdit_A.png" alt="" width="650;">
<img src="spatEdit_B.png" alt="" width="650;"></br>

The SpatEdit plug-in is intended to be used with two instances. The first instance of the plug-in allows the user to place markers on an equirectangular representation of the sphere. Alternatively the markers can automatically follow the directions of sound sources through use of the tracker. The source beamformer signals are then outputted by the first instance of the plug-in (A), where the user can then apply any conventional single-channel audio effect, re-balance their levels, or re-order the signals. These manipulated beamformer signals are then passed to the second instance of the plug-in (B), which also receives the residual signals from the first plug-in instance internally, and the COMPASS synthesis is conducted to obtain the output SH signals. Alternatively, the residual stream signals may be outputted by the first plug-in instance instead (and the beamformer signals passed internally to the second plug-in instance), which instead allows conventional linear  Ambisonics transformations to be applied to only the ambient parts of the scene.
  
This plug-in was developed by Leo McCormack and Archontis Politis.
    
### Gravitator
<img src="GravitatorGUI_alpha6_src%2076%200%20%20-24%2045%20-80%20-30.png" alt="" width="650;"></br>

A spatial focussor which pulls only the directional components of the sound scene towards user defined markers, with a certain degree of "gravitational-pull". The Ambient components of the sound scene remain unaltered.
  
This plug-in was developed by Leo McCormack and Archontis Politis.
     
## About the developers
    
* **Leo McCormack**: a doctoral candidate at Aalto University.  
* **Archontis Politis** post doctorate researcher at Tampere University, specialising in spatial sound recording and reproduction, acoustic scene analysis and microphone array processing.  
    
## References

<a id="ref_compass"></a>[1] Politis, A., Tervo S., and Pulkki, V. (2018) <a href="http://research.spa.aalto.fi/projects/sparta_vsts/publications/politis2019compass.pdf"><b>COMPASS: Coding and Multidirectional Parameterization of Ambisonic Sound Scenes.</b></a> <br> IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP).
    
[2] Pulkki, V. (2007) <b>Spatial sound reproduction with directional audio coding.</b> <br> Journal of the Audio Engineering Society 55.6: 503-516.
    
[3] Pulkki, V., Politis, A., Laitinen, M.-V., Vilkamo, J., Ahonen, J. (2017). <b>First-order directional audio coding (DirAC).</b> <br> <i>in</i> Parametric Time-Frequency Domain Spatial Audio, Wiley, p.89-138.
    
[4] Berge, S. and Barrett, N. (2010). <b>High angular resolution planewave expansion.</b> <br> 2nd International Symposium on Ambisonics and Spherical Acoustics.
    
<a id="hodirac_2015"></a>[5] Politis, A., Vilkamo, J., and Pulkki, V. (2015). <b><a href="http://research.spa.aalto.fi/projects/sparta_vsts/publications/politis2015sector.pdf"><b>Sector-based parametric sound field reproduction in the spherical harmonic domain.</b></a></b> <br>
    IEEE Journal of Selected Topics in Signal Processing, 9(5), 852-866.

<a id="hodirac_2017"></a>[6] Politis, A., McCormack, L., and Pulkki, V. (2017, October). <b><a href="http://research.spa.aalto.fi/projects/sparta_vsts/publications/politis2017enhancement.pdf"><b> Enhancement of ambisonic binaural reproduction using directional audio coding with optimal adaptive mixing</b></a>.</b> <br> In 2017 IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA) (pp. 379-383). IEEE.

    <p>[7] Politis, A. and Pulkki, V. (2017). <b>Higher-Order Directional Audio Coding.</b> <br>
    <i>in</i> Parametric Time-Frequency Domain Spatial Audio, Wiley, p.141.</p>

    <p>[8] Wabnitz, A., Epain, N., McEwan, A., Jin, C. (2011). <b>Upscaling ambisonic sound scenes using compressed sensing techniques.</b> <br> IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA).</p>
    
    <p>[9] Kolundzija, M., and Faller, C. (2018). <b>Advanced B-Format Analysis.</b><br> Audio Engineering Society Convention 144.</p>
    
    <p>[10] Sch&ouml;rkhuber, C., and H&ouml;ldrich, R. (2019, March). <b>Linearly and Quadratically Constrained Least-Squares Decoder for Signal-Dependent Binaural Rendering of Ambisonic Signals.</b> 
        <br> <i>in</i> Audio Engineering Society Conference: 2019 AES International Conference on Immersive and Interactive Audio. Audio Engineering Society. </p>
    
    <p>[11] S&auml;rkk&auml;, S., Vehtari, A. and Lampinen, J., 2004, June. <b>Rao-Blackwellized Monte Carlo data association for multiple target tracking. </b> <br><i>in</i> Proceedings of the seventh international conference on information fusion (Vol. 1, pp. 583-590). I.</p>
    
