# colorclassic_video_processor
Project for the reverse-engineering of the Macintosh Color Classic's CRT video processor
# Color Classic Video Processor
#
colorclassic_video_processor is an ongoing reverse‑engineering project to recreate the functionality of the XC1186B video processor found on the Macintosh Color Classic analog board by designing a replacement PCB that is pin‑compatible with the XC1186B. The goal is not a circuit‑for‑circuit replica but a practical drop‑in replacement that reproduces the processor’s essential behavior (with some features intentionally simplified or omitted and the possibility of adding new capabilities). Development has progressed to the point where the vast majority of features have been implemented, enabling a Color Classic to generate all required CRT signals for 640×480 VGA operation on machines that were previously modded for that mode. Other resolutions should work, as well, but have not yet been tested. The horizontal deflection pulse, vertical deflection sawtooth waveform, and RGB pre-amps are some of the major circuit subsystems that have been implemented. With little available documentation on the XC1186B itself, functionality had to be initially infered through a long process of signal measurement, route tracing, enabling/disabling various circuit sections, and reproduction of parts of the analog board's schematic. (See my latest partial analog board schematic [here](https://github.com/jonschultz/colorclassic_video_processor/blob/main/CC_analog_video_section_20260513A.pdf)). Much of that work will be documented here, albeit most of it after the fact. As of May 2026, multiple revisions of a home-made prototype PCB with hand-assembled components have been tested and modified with ongoing improvements and optimization. The latest is "Version3". More work might be done in the future to add features, improve performance, and make the PCB design more production-friendly.<br><br>

## Current Capabilities (v3)
* Support for 640x480 resolution at 60Hz refresh on VGA-modded Color Classics<br>
* Brightness and Contrast adjustment functional by way of MacOS software controls, such as through the "Screen" control panel. Contrast adjustments are also functional by way of the front bezel buttons.<br>
* Large dynamic range adjustment of individual RGB channel gain is available using on-board potentiometers.<br>
* Large dynamic range coarse adjustment of vertical height is available using an on-board potentiometer. The "VH" pot on the rear of the analog board is also functional for fine-tuning.<br>
* All geometry adjustment functions by way of the Color Classic's analog board rear potentiometers are functional.<br>
* Many of the color adjustment functions by way of the Color Classic's analog board rear potentiometers are currently functional, except for "Green Gain" and "Blue Gain".<br>
* Very high bandwidth RGB preamps on-board, providing very sharp images and exceptional color reproduction.<br>
* Additional on-board geometry adjustment for "warp", using input from the TDA8145 IC on the Color Classic analog board.<br><br>

## A Word about Specs and Compatibility
* It's currently difficult to know exactly what voltages or signals are within tolerance for inputs and outputs of the XC1186B. I can only work based on what are assumed nominals generated/received by the Color Classic. However, my hope is that colorclassic_video_processor would also work with other Macintoshes that also use the XC1186B, but I haven't done any testing with those systems, nor measured any of their associated signals/voltages.<br>
* The XC1186B is supplied with 8V and 24V (the latter, albeit, with relatively high output impedance) from the Color Classic's analog board. Like much of the inner workings of the XC1186B, I'm not sure how it uses those supplies internally. The 8V is definitely required to run most, if not all, of the subcircuits. In colorclassic_video_processor, I make use of the 8V for all the supply power, and no use of the 24V. There are multiple reference and supply voltages that I internally derive from the 8V. I've tried to make the circuitry tolerant to some variation and noise on the 8V supply, but it's not completely agnostic to the precise supply voltage. Geometry will vary slightly over the range of at least a few hundred millivolts, which can, of course, be corrected with the usual adjustments. This might be a difference from the behavior of the XC1186B, but again, I'm not sure how its supply voltages are spec'ed. The design is certainly open to the possibility of simple changes that could accomodate a wider supply voltage range or different nominal, if those applications ever arise.<br>
* colorclassic_video_processor will draw from about 600mW to 800mW of power from the 8V supply under normal conditions. This can vary as a function of resolution, brightness, contrast, and other factors.<br><br>

## Coming Soon
* Support for other common resolutions, including 512x384 and 800x600, with less adjustment required between resolution/mode changes.<br>
* Possible support for the "Green Gain" and "Blue Gain" analog board potentiometers.<br>
* See [Future and Ongoing Work](future.md)<br><br>

#
![PCB1](PCB_sideA.PNG)
<br>
CNC-prototyped, hand-assembled PCBA. The outline of the PCB is quite unusual, in order maximize board area within the video "cage", while providing clearance to other nearby discrete components.
<br><br><br>
![PCB2](PCB_sideB.PNG)
<br>
Bottom side of the PCBA, showing pins and additional circuitry.
<br><br><br>
![socket1](video_socket1.PNG)
<br>
The video "cage" on the analog board, showing the original XC1186B removed and 2x 21 pin sockets installed for quick installation and removal of the custom PCBA.
<br><br><br>
![socket1](PCB_installed2.PNG)
<br>
The custom PCBA installed in the sockets.
<br><br><br>
![boot](boot1.PNG)
<br>
Running with the colorclassic_video_processor, during boot.
<br><br><br>
#
[Image Gallery](gallery.md)
<br>
[Main Schematic and Sub-Circuits](sub_circuits.md)
<br>
[Fabrication Files and Notes](fabrication.md)
<br>
[Installation and Setup](setup.md)
<br>
[Future and Ongoing Work](future.md)
<br>
