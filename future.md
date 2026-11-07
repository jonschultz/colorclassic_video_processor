# Future and Ongoing Work
* In the spirit of providing more drop-in compatibility, if there is any outside interest in enabling the Blue Gain and Green Gain pots on the analog board (the only two that are currently non-functional with colorclassic_video_processor) I might work to implement it. I doubt that I would eliminate the gain pots that are on-board, since I personally think this is an upgrade due to the large dynamic range and 3-channel independent control. More likely, I would enable the Blue Gain and Green Gain pots to provide a little bit of fine control, in parallel with the full-range control of the onboard pots, similar to I've implemented Sub Contrast.<br><br>


## Development History
* 11/7/2026 - Released v4.2.2 for download. This is functionally identical to 4.2.1 (identical layout), but with some differences in part specs.<br><br>
* 11/1/2026 - Received PCBs for v4.2.1, completed assembly and started testing. Works as expected, however I discovered that some of the BJTs that I've spec'ed in the design files are not exact matches for the parts that I've been using in development. This leads to some small timing differences that affect horizontal centering, especially at frequencies other than 31.5kHz. I'm in the process of re-spec'ing these parts and will soon release v4.2.0.<br><br>
* 10/21/2026 - Ordered PCB fab for v4.2.1. New version includes a minor routing fix and a more appropriate connector the the VGA output. If the board tests well once received and assembled, I'll create a new downloadable release for this version.<br><br>
* 9/10/2026 - Received PCBs from vendor for v4.2.0 for testing. Design works with very minor rework to fix a routing error. New VGA output capability functions as expected. I'm currently implementing some cleanup as v4.2.1. I might release this one soon as a downloadable package.<br><br>
![4.2.1](images/4.2.1_A.PNG)<br><br>
* 8/18/2026 - Working on layout of v4.2.0 with on-board connector for VGA output.<br><br>
![vga_conn1](images/4.2.0_vga_conn1.PNG)<br><br>
* 8/12/2026 - Proof of concept for VGA output capability demonstrated with design mods and rework on a 4.0 PCB.<br><br>
![mirror1](images/mirror1.PNG)<br><br>
![mirror2](images/mirror2.PNG)<br><br>
* 7/26/2026 - Version 4.0.1 design released publicly.<br><br>
* 7/21/2026 - I've received the v4 PCBs from the fab, and I've got one assembled and running. Performance looks good and prety much identical to the reworked v3 prototype. However, I've already made some small changes to a few component values and some other minor changes in the horizontal section for further reduced temperature sensitivity. I plan to package up the KiCad files, BOM, and Gerbers + drill files for v4.0.1 and post them within the next few days. This will also mean that I'll need to clean up all the other sections of the repo to reflect the latest design. It's a lot of work, but it's coming.<br><br>
![PCB_v4_1](images/PCB_v4_1.PNG)<br><br>
![PCB_v4_2](images/PCB_v4_2.PNG)<br><br>
* 7/3/2026 - Completed porting the v4 design to KiCad, and now in the process of getting PCBs made externally. After initial assembly and testing, I plan to update all the documentation and post output files for v4, including Gerbers for PCB fabrication. v4 features will include:<br><br>
    * Better support for various resolutions and timings by normalizing horizontal and vertical adjustment ranges accordingly.<br>
    * PLL-like horizontal timing synchronization for reduced drift and horizontal shift effects across a frame (such as due to pincushion correction). Eliminates the need for a special connection to the TDA8145.<br>
    * Eliminates the additional coarse vertical adjusment potentiometer.<br>
    * Cleaner routing using standard PCBA design rules.<br><br>
![kicad](images/kicad_conversion1.PNG)<br><br>
* 6/27/2026 - v4 design is complete and I'm in the process of converting the project over to KiCad. The next design and output files that I post here will hopefully be output files from KiCad for easy PCBA fabrication.<br><br>
* 6/20/2026 - Further improvements to the phase correction in the horizontal circuitry have been prototyped and are working well. It has improved capability to detect the horizontal frequency and scale certain signals accordingly, requiring even less adjustment when switching resolutions. I've also implemented similar scaling in the vertical circuitry, though there's still some work to be done there for v4.<br><br>
![rework](images/horiz_rework1.PNG)<br>
v3 PCBA with rework and additional proto-board to experiment with v4 changes.<br><br>
* 6/6/2026 - I've prototyped changes to the horizontal circuitry on v3 to measure and regulate the phase of the horizontal drive pulse relative to the flyback pulse, providing PLL-like functionality. This goes beyond even the function mentioned above, removing many of the horizontal shift drift effects. It also makes the system even more agnostic to various resolutions and associated horizontal frequencies, and eliminates the need for a signal from the TDA8145 for "warp compensation". I'm working on more testing and optimization. I hope to have a v4 layout done in the next couple of weeks.<br><br>
* As of 5/26/2026, I've been experimenting with design changes and rework of the published v3 design to change the horizontal drive timing architecture. I have it basically working with timing referenced to the current scanline's HSYNC pulse, while also controlling the duty cycle more accurately. This makes the system much more tolerant of changes to the horizontal frequency, enabling 512x384, 640x480, and 800x600, with only some adjustment of the Horizontal Shift ("HS") potentiometer.<br><br>

