# Layout and Fabrication
<br>

![layout_front](images/layout_A_v4.2.2.png)
<br>

![layout_back](images/layout_B_v4.2.2.png)
<br>

![layout_3D](images/layout_3D_A_v4.2.2.png)
<br>

![layout_3D_back](images/layout_3D_B_v4.2.2.png)
<br><br><br>


## Parts List
<br>
As mentioned in another section, the part identifiers have evolved organically along with the circuit design. The ordering doesn't have much relationship to the circuit layout at this point.<br><br>
As part of the v4.2.2 changes, I've moved away from the S(S)8050 and S(S)8550 BJTs used in most of the circuitry. I've used a mix of suppliers of these parts (some not very well defined) and I've seen a range of device parameters. It's seems difficult to guarantee tight tolerance specs for these parts in general. Also, the SS versions (higher collector current) that I had spec'ed previously are not good drop-in substitutes for the low-current versions in much of the design, due to significantly higher leakage current and base-emitter capacitance. I've tested several substitutes, and the BC847C and BC857C parts have excellent performance, are cheap, and are easy to source. Using the "C" gain class is important, however. Some areas of the design require higher collector current, and BC847C is not quite good enough in this regard. I've maintained use of FMMT449 in a couple of places (Q4 and Q14), although this part is getting harder to source. I'm sure other parts with similar specs would be adequate substitutes, but I've haven't tested many. For the very high-bandwidth sections of the circuit, mainly in the RGB pre-amp section, RF BJT parts are spec'ed.<br><br>
Many of the components are commodity SMD parts, such as the resistors, so no part number is given, just specs. I would recommend using 1% fixed resistors whenever possible, as the cost is really quite negligible.<br><br>
Some of the capacitors absolutely require C0G dielectric for temperature stability and voltage insensitivity. A part number is explicity called out for all the capacitors. Other similar parts should work, as long C0G dielectric is used where specified.<br><br>
The BOM is too long to provide in a table on this page, so I've provided a CSV file here:<br>

[BOM](https://github.com/jonschultz/colorclassic_video_processor/blob/main/downloads/ccvp_v4.2.2.csv)
<br>

<br><br>

## Fabrication Details:
* Not all of the 42 pins of the original XC1186B footprint are utilized, as some of these simply connect to discrete components on the AB that I'm not using in my design. There are also sections that I haven't fully implemented, like horiztonal deflection shutdown for X-ray protection, making use of Pin 30.<br><br>
* The Mill-Max pins on the board could be directly soldered to the Color Classic's analog board after the XC1186B is de-soldered an removed, but I highly recommend using a socketed connection instead. This will make debugging and rework much easier. I used two of the Preci-dip 317-87-121-41-005101 sockets, which are needed for the two rows of 21 pins locations. These use the correct 1.78mm pitch of the XC1186B, and their pin diameters are compatible with the AB's through holes.<br><br>
* Some regions of the circuitry involve fairly high impedances, especially in the RGB pre-amp section. As such, even small current leakage from flux residue can reduce performance. It's important to wash away all flux residue after PCB assembly, if you are doing your own hand-assembly. The same applies the analog board after desoldering the XC1186B.<br><br>
* I've provided a zip file with the fabrication files (Gerbers and drill files) for v4.2.2, which can be directly uploaded to a PCB fab house like PCBWay. I've also provided a zipped archived set of KiCad design files. Everything here is provided under a Creative Commons license, allowing anyone to reuse/remix this work for non-commercial purposes. You can also download the output files at my PCBWay project page, or order PCBs/PCBAs directly there. You can find the page <a href="https://www.pcbway.com/project/shareproject/colorclassic_video_processor_e97f29b9.html">here.</a><br><br>
<a href="https://github.com/jonschultz/colorclassic_video_processor/">colorclassic_video_processor</a> © 2026 by <a href="https://github.com/jonschultz/colorclassic_video_processor/">Jonathan Schultz</a> is licensed under <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/">CC BY-NC-SA 4.0</a><img src="https://mirrors.creativecommons.org/presskit/icons/cc.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/by.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/nc.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;"><img src="https://mirrors.creativecommons.org/presskit/icons/sa.svg" alt="" style="max-width: 1em;max-height:1em;margin-left: .2em;">

[KiCad Design Files](https://github.com/jonschultz/colorclassic_video_processor/blob/main/downloads/ccvp_v4.0.1.zip)
<br>
[Gerber Files](https://github.com/jonschultz/colorclassic_video_processor/blob/main/downloads/ccvp_v4.0.1_gerber.zip)
