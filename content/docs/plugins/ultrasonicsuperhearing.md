---
title: "UltrasonicSuperHearing"
description: "Plug-in description for the UltrasonicSuperHearing."
lead: "Plug-in description for the UltrasonicSuperHearing."
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 170
toc: true
---

## Plug-in description

<img src="UltrasonicSuperHearing_PluginGUI.png" alt="" style="max-width: 65%"/></br>

Ultrasonic sound sources are inaudible to humans. While there do exist devices that can capture, pitch shift and reproduce ultrasonic sound sources for humans to listen to, they generally only employ a single microphone and loudspeaker. Therefore, the listener is unable to localise where these pitch shifted ultrasonic sound sources are located.

However, by instead capturing the ultrasonic sound sources using an array of microphones, it is possible to estimate their direction of arrival (DoA), and use this information to spatialise a pitch shifted signal in this direction. Therefore, not only is the listener able to perceive these ultrasonic sound sources, but they are also able to localise them in the correct direction.

## Building a suitable ultrasonic microphone array

The CAD files and drawings used for 3D printing the 6 sensor proof-of-concept array, which was employed for the study detailed in [1], can be found in the companion [**git repository**](https://github.com/leomccormack/Super-Hearing) folder. Further details regarding its construction can also be found in the paper.

<img src="UltrasonicArray.png" alt="UltrasonicArray" width="450"/></br>

## Auralising the captured ultrasonic sound sources

The audio plugin renders the 6 microphone signals to the 2 binaural channels. It employs the DoA estimation, pitch-shifting, and binauralisation, as described and used for the listening tests conducted in [1].
 
<img src="UltrasonicArray_ProcessingDiagram.png" alt="" style="max-width: 85%"/></br>


## Demo

The proposed ultrasonic super-hearing system is demonstrated in the following video:

<iframe width="560" height="315" src="https://www.youtube.com/embed/HMkZs7a1nQc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

(Please wear headphones)

## About the authors
    
* **Leo McCormack**: a doctoral candidate at Aalto University.
* **Ville Pulkki**: Professor at Aalto University, known for VBAP, SIRR, DirAC and eccentric behaviour.
* **Raimundo Gonzalez**: a doctoral candidate at Aalto University.

## License

This application may be used for academic, personal, and/or commercial use. The source code may also be used for commercial purposes, provided that the terms of the GPLv3 license are fulfilled. This requires that the original code and/or any derived works must also be open-sourced and made available under the same GPLv3 license, if it is to be used for commercial purposes.

## References

* [1] Pulkki, V., McCormack, L. & Gonzalez, R. 2021. [**Superhuman spatial hearing technology for ultrasonic frequencies**](https://www.nature.com/articles/s41598-021-90829-9). Scientific Reports 11, 11608 (2021). https://doi.org/10.1038/s41598-021-90829-9