# Installation and Setup
<br>

## Preparing the Board
* After PCBA assembly, it's a good idea to set the potentiometers to rough nominal positions to get a good image, prior to installation and first startup. Experimentally, I've found that setting the blue and green gain trim pots so that the low side to wiper resistance is about 600 ohms is a good starting point. For red, this is around 450 ohms. These values can be measured in-circuit (no need to do it prior to soldering the pots onto the board) as the adjustment is made. As will be discussed below, the RGB gain adjustments can also be done live when the system is running.<br><br>
* The warp (SKEW_POT) adjustment can also be made prior to adjustment, though it might take some trial and error to set it correctly once the system is running, as will be discussed below.<br><br>
* See the Fabrication section for details on installing sockets into the analog board. I'll assume here that this has been completed.<br><br>
* One other detail related to preparation of the analog board is that film capacitors CF4 and CL36 (see the image below) either need to be removed or bend off. These caps will otherwise interfere with the colorclassic_video_processor board, and working around them with a reduced board outline would have been too constraining. These caps serve no purpose with the XC1186B removed, so there's no hard in bending them or fully removing them. I've simply bent mine over, in case I ever need them in the future.<br><br>
![bend](cap_bend1.PNG)
<br>


## test
