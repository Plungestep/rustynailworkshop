---
layout: post
title: Do-It-Yourself Blu-Ray Laser Pointer (Part 2)
tags: [frontpage, electronics, experiment]
image: '/images/posts/2009-3-12/laser.jpg'
---

Everything I had read thus far told me that I needed a circuit which supplied a constant current to the laser diode.  It would have been easier if I could have just connected the laser diode to my DC power supply and adjusted the voltage, but that would have been too easy.

By the way, this is the second of a two part series on this project.

I’m not very good at designing my own electronic circuits, so I thought I’d cruise the internet to see if someone had put one together already.  Sure enough, I found a circuit Joey Hagedorn’s web site.  Apparently he tried something similar to this project, but with a different laser pointer.
<p align="center">
  <img src="/images/posts/2009-3-12/circuit.jpg">
</p>
CircuitThe circuit I ended up using is shown above.  I ordered all of the parts from [Digikey.com](http://www.digikey.com/), which came to $4.60, which included $2.02 in postage (U.S. Postal Mail).  I love this company, they have what I need and they shipped the parts out fast!

Here is what I purchased for the circuit:
* One LM317TFS-ND IC Regulator (adjustable)
* One 47 uF capacitor (P802-ND)
* One 10 uF capacitor (P807-ND)
* One 0.1 uF capacitor (P820-ND)
* One 100 Ohm potentiometer (3309W-101-ND)
* One 15 Ohm resistor (CMF15.0HFCT-ND)
* One diode (1N4002GOS-ND)

I wired everything up on a breadboard that I had from a previous project, and I even set up the circuit to match the schematic shown above.  
<p align="center">
  <img src="/images/posts/2009-3-12/meter.jpg">
</p>
As you can see from the photo, I used a common red LED I had to test the operation of the circuit.  Sure enough, the LED lit up (although it was very dim), and I even had my multimeter connected to measure the current in the circuit.  The LED would draw anywhere from 5-10 mA from my circuit.  I adjusted the potentiometer to somewhere in the middle and increased the voltage from my DC power supply to 8 volts.  No change in the LED brightness, which means my laser diode would be safe at 8 volts DC.

I then tried to find out from [Sam’s Laser FAQ site](http://donklipstein.com/laserdio.htm#diotoc) which pins on my laser diode were supposed to be used for each connection.  The site is a good site, but has too much information, and I just wanted to get started.  I made a guess and wrote it down.

Next, I put on some laser safety goggles that I had previously purchased (for another project) just in case this laser diode was bright enough to damage my eyes.  I also set up my video camera to make sure I could see the beam if it emitted infrared light instead of visible light.  I made a guess for my connections and connected the Blu-Ray diode to my circuit.

Nothing happened.  Maybe I had a loose wire?  Nope.  I also noticed that my meter wasn’t detecting any current.  I tested the circuit again with the red LED.  Yes, it worked just fine.  I then began the process that any experimenter tries when something doesn’t work right.  I started connecting the positive and negative wires to any of the three leads I could, hoping that I just had my laser diode pins identified incorrect.  After about five different combinations, I found one that emitted blue light.  It worked!
<p align="center">
  <img src="/images/posts/2009-3-12/test.jpg">
</p>
I was a little surprised to see that the blue light being emitted wasn’t focused into a reasonable beam.  I guess I should have expected this, but I was surprised none the less.  The blue color doesn’t photograph well, but you get the picture.  The real color isn’t that much more impressive, so you’re not missing much.
<p align="center">
  <img src="/images/posts/2009-3-12/close_up.jpg">
</p>
I grabbed the lens assembly I had saved from the Sharp Blu-Ray player and put it in front of the beam.  Neither lens on this assembly focused the beam down like I wanted, so I found another lens I had lying around.  That didn’t work either.  I’m going to have to work a little harder to figure out how to focus this beam down, but at least I have a working blue laser!

The working laser.At the end, I noticed that my multimeter was measuring 25 mA of current.  I adjusted the potentiometer upwards and the meter went up to 30 mA.  I think this is a safe level for continuous operation, as explained by others who tried this same experiment.
