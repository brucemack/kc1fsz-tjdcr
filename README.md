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
circuit. This is a completely *pure* TJ-DCR, but using modern construction techniques 
including a commercial PCB, SMD components (mostly 0805), and the most compact layout
I could come up with.

![System Picture](docs/pcb-1.png)

Once the testing is complete I will make the PCB/BOM available for anyone who wants
to try it.

Modification Notes
==================

* IMPORTANT: My part reference numbers don't match those in the official schematic.
Sorry!!
* I am using T37-6 toroids in a few places where Bill/Dean used T50-6. 
* I am using Schottky diodes since those were in the original TJDCR rig. I noticed
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






