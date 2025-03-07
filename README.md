Overview
========

This is my compact PCB implementation of the famous Thomas Jefferson Direct Conversion Receiver
designed by Bill Meara (N2CQR) and Dean Souleles (KK4DAS). Full documentation for the 
original rig [can be found here](https://hackaday.io/project/190327-high-schoolers-build-a-radio-receiver). This project has been discussed at length
on the excellent Solder Smoke Podcast and in a detailed series of videos that can be found
[starting here](https://www.youtube.com/watch?v=rLjxU2rMeXw). I would particularly 
encourage you to watch Dean's superb tutorial series on YouTube. 

I built this rig as part of the "Direct Conversion Challenge" issued by Bill and Dean. As
stipulated by Bill/Dean, I am resisting all temptations to modify/improve the original 
circuit. However, technically speaking this is not a *pure* TJDCR since there 
are a few departures from the recommended construction techniques and part selections. 
Importantly, I am using modern construction techniques including a commercial PCB (single board), SMD 
components (mostly 0805), and the most compact layout I could come up with. My KiCad model is provided
here for anyone who wants to experiment with it.

A huge thanks to Scott KQ4AOP for creating and sending me the tuning form 
needed to build the PTO! You also need a brass 1/4-20 bolt around 2.5" long and two 1/4-20 nuts.

Here's a demo video of the working rig:

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/tszAnfJriHQ/0.jpg)](https://www.youtube.com/watch?v=tszAnfJriHQ)

Here's the KiCad rendering of my board.  The part reference numbers are correct
in this picture:

![System Picture](docs/pcb-1.png)

Here's what the raw PCB it looks like in real life. *The part reference numbers didn't 
match Bill/Dean's schematic in this version of the board* so don't get confused.  The KiCad model was later updated 
to fix this and the 2025-03 board has the correct reference numbers.

![System Picture](docs/IMG_1835.jpg)

Here's the populated board:

![System Picture](docs/IMG_183.jpg)

And the full rig:

![System Picture](docs/IMG_1832.jpg)

> [!IMPORTANT]  
> I know the purists may raise objections, so I would like to emphasize the value
> of building the TJDCR rig from Bill/Dean's exact specifications *first* before getting into 
> modifications including (but not limited to) PCBs and SMDs. The main point of the TJDCR
> project is to learn the process of building from scratch, and using a commercially
> fabricated PCB
> somewhat defeats that purpose. I've built DCR rigs a few times (as well as several SSB transceivers) using traditional Manhattan/Ugly (aka Beauty) 
> style so I'm trying to do something a bit different for fun. That being said, we are 
> moving into a new world where many components of value to radio homebrewers are not 
> available in through-hole packages. I would encourage everyone get over their
> fears of surface-mount parts, buy a decent headband magnifier, and start practicing 
> SMD-homebrew. I've found that by modifying the stock IPC-7351 0805 footprints provided in
> KiCad to 
> extend the pads outward 0.5mm or so you can use a normal soldering iron with a fine tip with 
> no problems.

Once the testing is complete I will make the PCB/BOM available for anyone who wants
to try building it in this style.

My [KiCAD schematic is here](https://github.com/brucemack/kc1fsz-tjdcr/blob/main/hw/tjdcr-1/plots/tjdcr-1.pdf) if you want to have a look. I've tried to use the official TJDCR part reference numbers
as much as possible.

Modification Notes
==================

This will probably get me into trouble, but I've deviated in a few places. I believe 
I've maintained the spirit of the original circuit. :grin:

* This is a single board design, whereas Bill/Dean recommend 4 boards to promote modularity.
You will note that I've silk-screened borders around the 4 modules on my board to 
emphasize the modularity of the original design. I have included test points on the 
PCB and I assemble/test the circuit in the recommended modules to simplify debug.
* I'm using ceramic non-polarized capacitors in some places where Bill/Dean used
polarized electrolytic caps.
* I'm not using the recommended silver/mica caps in my oscillator, primarily because
of size constraints. The first iteration of the build used NP0 caps and stability looked
pretty good. I strongly suspect that the compact "hardened" PCB eliminates some of the variability 
experienced in the Manhattan/Ugly construction so oscillator stability may be less of an 
issue. I'm doing some more experiments and will provide a write-up on my findings later.
* I am using T37-6/FT37-43 toroids where Bill/Dean used T50-6/FT50-43. This requires 
thinner wire and a great deal of winding patience. I think the board can physically handle the T50s 
if necessary. 
* I did not put in a trimmer for the top coupling capacitor in the band-pass filter. I'm 
comfortable with a cut-and-try approach on that component given how it impacts the shape
of the filter. Trimmers on the shunt caps are critical given the variability in the 
toroidal inductors.
* I am using Schottky diodes in the mixer since those were in the original TJDCR rig. I noticed
a later change to the 1N4148 switching diode, but I have not made that change yet.
* Note the "LO Option" connector on the board, which is not in the original 
schematic.  Normally the two pins on this connector
should be jumpered together, but those wanting to inject external VFOs may want to 
open this connection and attach the external frequency source to pin 1. This 
is also a good place to connect a frequency counter or to bridge the VFO to the 
companion transmitter module.
* There are a few extra parts (C40-C41, R40-R41) in the schematic to support a frequency offset 
feature that is described in SSDRA (page 218 figure 4). This is used to drive 
a companion CW transmitter module. Don't plug in C40 when you 
are building the stock TJDCR.

Layout Notes
============

* The space under the frequency-determining components of the VFO has been
cleared on all layers. I've read in a few places that this improves VFO 
stability by removing the large (temperature-variable) capacitor that is 
formed between the PCB copper layers.
* Via fencing is used throughout the board to isolate the VFO and the audio
amplifier from everything else.
* THe power/ground connections are intentionally placed close to the power
stage of the audio amplifier to keep these relatively large currents away
from the earlier stages.

Tools
=====

I am using KiCAD V9 for the schematic capture and PCB layout.

Current Areas of Experimentation
================================

* The first iteration used a 4-layer PCB stackup since that provides the best
RF performance. As it turns out, there is very little routed on the bottom layer and 
the +9V routing is pretty simple. Plus, at 7 MHz a lot of this probably doesn't matter. I am 
going to create a 2-layer version of the layout to shave a 
few dollars and see if this makes any measurable difference. The 4-layer boards cost $1.40
each so we're not talking about a big difference here. 2-layer boards are also more easily
made by the fabs in the US. Unfortunately, I've not found an onshore fab that can do 4 layers as
quickly/cheaply as the offshore providers, which brings up a number of geopolitical issues. (Side
note: Thomas Jefferson was a strident global free-trade advocate.)
* The initial form-factor uses what I call a "half PCB": 100mm x 35mm.
That's half of the 100mm x 70mm size that cheap copper-clad PCB stock usually comes in.
I'm thinking of reworking the layout a bit to get into the more squarish 90mm x 50mm form-factor 
that is needed to fit into a Peppermint Altoids tin. Major QRP street cred possible here.
* I also like the super-small binocular BN43-2402 ferrite cores and will be testing
those on the mixer stage in the next iteration.
* I have a companion CW transmitter module I call "James Madison" which I will 
document later.

Bill Of Materials (2025-03 Version)
===================================

This parts list is provided for informational purposes.  I don't have part numbers for a lot of the
generic components because I have a collection of those on hand. I like the 0805 SMD resistor and 
capacitor "books" since they contain anything you could ever want. The more unique parts can be
ordered from Digikey using the part numbers provided. The audio transformer is a Mouser-only part.
The 2.54mm headers are cut from a long header strip.

| Reference	| Value	| Notes |
| --------- | ----- | ----- |
| C1,C2 | 660p | NP0 Ceramic 0805 |
| C3 | 130p | NP0 Ceramic 0805 |
| C4,C5,C6,C7,C21,C41 | 0.1u | Generic Ceramic 0805 |
| C8,C14,L2 | 10u | Generic Ceramic 0805 |
| C9,C11,C13 | 470u 10V | Tantalum in 7343 package, polarized (EX: Kyocera TPSE477K010R0100) |
| C10,C12,C15 | 47u | Generic Ceramic 0805 |
| C16 | 0.47u | Generic Ceramic 0805 |
| C17 | 33u | Generic Ceramic 0805 |
| C18,C19 | 150p | NP0 Ceramic 0805 |
| C20 | 10p | NP0 Ceramic 0805 |
| C40,C181,C191 | 6.5-30pF Trimmer | Manufacturer package (EX: EW Electronics GKG30086-05) |
| D1 | 8.2V 250mW Zener | SOT23-3 package (EX: onsemi BZX84C8V2LT1G) |
| D25,D34 | Schottky Diode Array | Pay attention to polarity, SOT23-3 package (EX: Diotec Semi BAT54S) |
| J1 | Antenna (50 ohms) | SMA connector female through-hole (EX: Amphenol 901-144-8RFX) |
| J2 | Tuning | Generic 2.54mm header |
| J3 | Power | Generic 2.54mm header | 
| J4 | LO Option | Generic 2.54mm header |
| J5 | Volume | Generic 2.54mm header |
| J6 | Speaker | Generic 2.54mm header |
| J7 | TX Offset | Generic 2.54mm header |
| L11 | 100u | 0805 package (EX: TDK MLZ2012N101LT000) |
| Q1,Q3,Q5,Q40 | NPN Transistor 3904 | SOT23-3 package (EX: onsemi MMBT3904LT1G) |
| Q2 | JFET Transistor J310 | SOT23-3 package (EX: onsemi SMMBFJ310LT3G) |
| Q4 | NPN Transistor 3904 | Generic TO-92 package |
| R1,R2 | 10k | Generic 0805 |
| R3 | 3.3k | Generic 0805 |
| R4,R6,R14 | 100R | Generic 0805 |
| R5 | 100k | Generic 0805 |
| R7 | 47R |	Generic 0805 |
| R8,R12,R16 | 14.7k | Generic 0805 |
| R9,R13,R17 | 4.7k | Generic 0805 |
| R10,R18 | 1k | Generic 0805 |
| R11,R19 | 470R | Generic 0805 |
| R20 | 220R | Generic 0805 |
| R40 | 47k | Generic 0805 |
| R41 | 2.2k | Generic 0805 |
| T1 | 5:28 Toroid transformer | Wound on T37-6 toroid, #28 wire |
| T2 | 5:28 Toroid transformer | Wound on T37-6 toroid, #28 wire |
| T3 | 1:1:1 Toroid transformer (trifilar) | Wound on FT37-43 toroid, #28 wire |
| T4 | 1:1:1 Toroid transformer (trifilar) | Wound on FT37-43 toroid, #28 wire |
| T5 | 8R:1k audio transformer| EX: Mouser 42TL013-RC |
