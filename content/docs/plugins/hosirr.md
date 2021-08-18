---
title: "HO-SIRR"
description: "Description for the HO-SIRR application."
lead: "Description for the HO-SIRR application."
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "plugins"
weight: 160
toc: true
---

## Application description
    
Higher-order Spatial Impulse Response Rendering (HO-SIRR) is a rendering method, which can synthesise output loudspeaker array room impulse responses (RIRs) using input spherical harmonic (Ambisonic/B-Format) RIRs of arbitrary order [<a href="../../help/related-publications/#mccormack2020higher"><b>1</b></a>,<a href="../../help/related-publications/#mccormack2019higher"><b>2</b></a>]. The method makes assumptions regarding the composition of the sound-field and extracts spatial parameters over time, which allows it to map the input to the output in an adaptive and more informed manner; when compared to purely linear methods such as Ambisonics. 

The idea is that you then convolve a monophonic source with this loudspeaker array RIR, and it will be reproduced and exhibit much of the spatial characteristics of the captured space. Note that the HO-SIRR algorithm is an extention of the original first-order SIRR formulation, first proposed back in 2005 [3,4], by employing the higher-order analysis principles described in [5].
    
Note that the HO-SIRR application is a direct port of the HO-SIRR MATLAB toolbox, which is slighly more configurable than the C/C++ implementation, and can be found <a href="https://github.com/leomccormack/HO-SIRR"><b>here</b></a>.  

<img src="HOSIRR_GUI.png" alt="" style="max-width: 85%"></br>

The suggested workflow is:
    
* Measure a room impulse response (RIR) of a space with a spherical microphone array (e.g. using <a href="http://eprints.hud.ac.uk/id/eprint/24579/?fbclid=IwAR1EorukJ1MaLojT4Eof8eTSOc9-A479kVhqbF7fHaSycOO7llAD7aIj3TA"><b>HAART</b></a>), and convert it into an Ambisonic/B-format RIR (e.g. using sparta_array2sh).
* Load this B-Format/Ambisonic RIR into the HOSIRR App/plug-in and specify your loudspeaker array directions and desired rendering configuration (although, the default should suffice for most purposes).  
* Click "Render", and then "Save", to export the resulting loudspeaker array RIR as a multi-channel .wav file.
* Then simply convolve this loudspeaker array RIR with a monophonic source signal, and it will be reproduced over the loudspeaker array (also exhibiting the spatial characteristics of the captured space). Plug-ins such as <a href="http://pcfarina.eng.unipr.it/X-volver.htm"><b>Xvolver</b></a>, <a href="http://www.angelofarina.it/X-MCFX.htm?fbclid=IwAR0AcjaXa_szrrJ4nFHn1lMk_6dmTd8WmcQwokyEb7eD0ULgHyHpoFtTFmk"><b>X-MCFX</b></a>, sparta_matrixconv (included in the installer), and <a href="http://www.matthiaskronlachner.com/?p=1910"><b>mcfx_convolver</b></a>, are well suited to this convolution task.
    
## Listening test results at a glance
    
The perceptual performance of HO-SIRR was evaluated based on formal listening tests in [1], where it was compared to Mode-Matching Ambisonics decoding. It was found that if the mono signal is quite stationary (such as a trombone recording), then first-order SIRR renderings can sound almost equivalent to 5th order Ambisonics. However, if the mono signal is more transient (such as a kick drum or speech sample), then the benefits of the higher-order SIRR renderings are revealed. For an in-depth description of the listening test and a discussion of the results, see: <a href="../../help/related-publications/#mccormack2020higher">[<b>1</b>]</a>.
    
<img src="JAES_orderTest_post_review.png" alt="" style="max-width: 100%"> </br>
     
## About the authors
    
* **Leo McCormack**: a doctoral candidate at Aalto University.
* **Archontis Politis**: post doctorate researcher at Tampere University, specialising in spatial sound recording and reproduction, acoustic scene analysis and microphone array processing.
* **Ville Pulkki**: Professor at Aalto University, known for VBAP, SIRR, DirAC and eccentric behaviour.

## License

This application may be used for academic, personal, and/or commercial use. The source code may also be used for commercial purposes, provided that the terms of the GPLv3 license are fulfilled. This requires that the original code and/or any derived works must also be open-sourced and made available under the same GPLv3 license, if it is to be used for commercial purposes.
    
## References
    
<a style="color:#000000">[1] McCormack, L., Pulkki, V., Politis, A., Scheuregger, O. and Marschall, M. (2020). <b> <a href="../../help/related-publications/#mccormack2020higher"><b>Higher-Order Spatial Impulse Response Rendering: Investigating the Perceived Effects of Spherical Order, Dedicated Diffuse Rendering, and Frequency Resolution</b></a>. </b> <br>Journal of the Audio Engineering Society, 68(5), pp.338-354.
    
<a style="color:#000000">[2] McCormack, L., Politis, A., Scheuregger, O., and Pulkki, V. (2019). <b> <a href="../../help/related-publications/#mccormack2019higher"><b>Higher-order processing of spatial impulse responses.</b></a></b> <br> Proceedings of the 23rd International Congress on Acoustics, 9--13 September 2019 in Aachen, Germany.
     
<a style="color:#000000">[3] Merimaa, J. and Pulkki, V. (2005). <b>Spatial impulse response rendering I: Analysis and synthesis</b> <br> Journal of the Audio Engineering Society, 53(12), pp.1115-1127.
 
<a style="color:#000000">[4] Pulkki, V. and Merimaa, J. (2006). <b>Spatial impulse response rendering II: Reproduction of diffuse sound and listening tests</b> <br> Journal of the Audio Engineering Society, 54(1/2), pp.3-20.
        
<a style="color:#000000">[5] Politis, A. and Pulkki, V. (2016). <b>Acoustic intensity, energy-density and diffuseness estimation in a directionally-constrained region</b> <br> arXiv preprint arXiv:1609.03409.