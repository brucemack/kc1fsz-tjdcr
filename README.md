Overview
========

This is a compact PCB implementation of the famous Thomas Jefferson Direct Conversion Receiver
designed by Bill Meara (N2CQR) and Dean Souleles (KK4DAS). Full documentation for the 
original rig [can be found here](https://hackaday.io/project/190327-high-schoolers-build-a-radio-receiver). This project has been discussed at length
on the excellent Solder Smoke Podcast and in a detailed series of videos that can be found
[starting here](https://www.youtube.com/watch?v=rLjxU2rMeXw). I would particularly 
encourage you to watch Dean's superb tutorial series on YouTube. 

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
> project is to learn the process of building from scratch, and using a commercially
> fabricated PCB
> somewhat defeats that purpose. I've built DCR rigs a few times (as well as several SSB transceivers) using traditional Manhattan/Ugly 
> style so I'm trying to do something a bit different this time. That being said, we are 
> moving into a new world where many parts of interest to radio homebrewers are not 
> available in through-hole packages. I would recommend that everyone get over any 
> fears of surface-mount parts, buy a good set of magnifying glasses, and start practicing 
> SMD-homebrew.

Once the testing is complete I will make the PCB/BOM available for anyone who wants
to try it in this style.

My [KiCAD schematic is here](https://github.com/brucemack/kc1fsz-tjdcr/blob/main/hw/tjdcr-1/plots/tjdcr-1.pdf) if you want to have a look. I've tried to use the official part reference numbers
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
* I am using T37-6 toroids in a few places where Bill/Dean used T50-6. This requires 
thinner wire and a great deal of winding patience. The board can physically handle the T50s 
if necessary. 
* I did not put in a trimmer for the top coupling capacitor in the band-pass filter. I'm 
comfortable with a cut-and-try approach on that component given how it impacts the shape
of the filter.
* I am using Schottky diodes in the mixer since those were in the original TJDCR rig. I noticed
a later change to the 1N4148 switching diode, but I have not made that change yet.
* Note the "LO Option" connector on the board, which is not in the original 
schematic.  Normally the two pins on this connector
should be jumpered together, but those wanting to inject external VFOs may want to 
open this connection and attach the external frequency source to pin 1. This point
is also a good place to connect a frequency counter.

Tools
=====

I am using KiCAD V8 for the schematic capture and PCB layout.

Areas of Experimentation
========================

* The first iterations are using a 4-layer PCB stackup since that provides the best
RF performance. As it turns out, there is very little routed on the bottom layer and 
the +9V routing is pretty simple. I am going to create a 2-layer version to shave a 
few dollars and see if this makes any difference. (NOTE: The 4-layer boards cost $1.40
each so we're not talking about big differences here.)
* The initial form-factor uses what I call a "half" PCB: 100x35mm.
That's half of the 100x70mm size that cheap copper-clad PCB stock usually comes in.
I'm thinking of reworking the layout a bit to get into the more squarish 90x50mm form-factor 
that is needed to fit into an Altoids tin. Major QRP street cred possible here.
* I also like the super-small binocular BN43-2402 ferrite cores and will be testing
those on the mixer stage in the next iteration.

References
==========






