Overview
========

This is a compact PCB implementation of the famous Thomas Jefferson Direct Conversion Receiver
designed by Bill Meara (N2CQR) and Dean Souleles (KK4DAS). Full documentation for the 
original rig [can be found here](https://hackaday.io/project/190327-high-schoolers-build-a-radio-receiver). This project has been discussed at length
on the excellent Solder Smoke Podcast and in a detailed series of videos can be found
[starting here](https://www.youtube.com/watch?v=rLjxU2rMeXw). I would particularly 
encourage you to watch Dean's tutorial series on YouTube.

I built this rig as part of the "Direct Conversion Challenge" issued by Bill and Dean. As
stipulated by Bill/Dean, I am resisting all temptations to modify/improve the original 
circuit. However, technically speaking this not a completely *pure* TJ-DCR since there 
are a few departures from the recommended construction techniques and part selection. 
Importantly, I am using modern construction techniques including a commercial PCB (single board), SMD 
components (mostly 0805), and the most compact layout I could come up with.

![System Picture](docs/pcb-1.png)

> [!IMPORTANT]  
> I know the purists will raise objections, so I would like to emphasize the importance/value
> of building the TJDCR rig from Bill/Dean's exact specifications *first* before getting into 
> modifications including (but not limited to) PCBs and SMDs. The main point of the TJDCR
> project is to learn the process of building from scratch, and using a commercial PCB
> somewhat defeats that purpose. I've built this rig a few times  (as well as several SSB transceivers) using Manhattan/ugly
> style so I'm trying to do something a bit different this time.

Once the testing is complete I will make the PCB/BOM available for anyone who wants
to try it.

Modification Notes
==================

* IMPORTANT: My part reference numbers don't match those in the official schematic.
Sorry!!
* This is a single board, whereas Bill/Dean recommend 4 boards to promote modularity.
You will note that I've silk-screened borders around the 4 modules on my board to 
emphasize the modules.
* I am using T37-6 toroids in a few places where Bill/Dean used T50-6. 
* I did not put in a trimmer for the top coupling capacitor in the band-pass filter. I'm 
comfortable with a cut-and-try approach on that component given how it impacts the shape
of the filter.
* I am using Schottky diodes in the mixer since those were in the original TJDCR rig. I noticed
a later change to the 1N4148 switching diode, but I have not made that change yet.
* Note the "LO Option" connector on the board, which is not in the original 
schematic.  Normally the two pins on this connector
should be jumpered together, but those wanting to inject external VFOs may want to 
open this connection and attach the external frequency source to pin 1. 

Tools
=====

I am using KiCAD V8 for the schematic capture and PCB layout.

References
==========






