---
layout: post
title: A Probotix CNC Machine
tags: [frontpage, electronics]
image: '/images/posts/2012-12-28/cnc.jpg'
---

One of my interests involves robotics, especially autonomous self-charging robotics. However, I realize most of my skills center around microprocessors, wood construction techniques, electronics, and some limited computer software skills. I knew I was missing the ability to make custom, metal and/or wood components for my various projects. Thus, the need arose for a CNC machine. If only I knew how to use one!

After some online research, I narrowed down my options to a [Shapeoko](http://www.shapeoko.com/) or a [Probotix Fireball V90](https://probotix.com/FireBall_v90_cnc_router_kit/).  The Shapeoko is significantly cheaper and everything is made with open source license rights.  The Fireball V90 uses some proprietary components, costs more, but has a stronger setup and is more capable than the Shapeoko.  After considering my needs, I decided I wanted to be able to carve and cut both wood and metal, focusing on aluminum.  I’ll need to dedicate space on my workbench for either of these two machines, and dust collection will be an issue for either one.  I understand I will need a separate computer if I purchase the Fireball V90, and I may need separate CAD software.  

Fast forward about a week, and I decided I would purchase the Probotix Fireball V90.  I ordered it with the necessary USB components because it would be rather hard to find a computer with a parallel port.  I selected the option for a Bosch palm router and ordered a PR20EVSK Bosch router from Amazon.com.  Oddly enough, Probotix also sells the Bosch router, but charges significantly more than Amazon for the same thing.  Probotix shipped my order quickly, although I feel sorry for the UPS delivery person since it weighs 64 pounds.  Incidentally, if you are planning to purchase a Bosch Colt palm router like I did, I suggest you read [this article](http://www.precisebits.com/lab_reports/bosch_colt_TIR.htm) first, which actively discourages them for CNC machine use.  Another item I wish I had known before order it.

A Probotix Fireball V90 CNC Machine.  Image from Probotix.com.
A Probotix Fireball V90 CNC Machine. Image from Probotix.com.
One of my initial concerns was the software that I would need, mostly because I didn’t have any and I didn’t know how to use it.  After much research, I understood that I would need CAD software to create the drawing of the part and CAM software to set out the tool paths so the CNC machine knew how to cut it out.  Probotix offers a cheap version of MeshCAM, which I purchased and will try it out.  As for the CAD software, I may initially try out AutoDesk’s Inventor Fusion (free from the Apple App Store for the Mac).  I’m not sure this package will supply the correct file format for MeshCAM to use, but I’ll try it.

The machine arrived a week or so after I ordered it, and everything came packaged in a single, and heavy, box.  They used quite a bit of broken-off styrofoam to package everything, which meant that most components needed to have little fragments of styrofoam vacuumed off before assembly.  Everything arrived safely, but I’m not a fan of styrofoam due to environmental concerns.

Assembly of the machine took most of the afternoon.  The instructions were posted on the Probotix web site, and were easy to follow.  The only step I did not like was the grinding of the stepper motor shafts so a set pin could attach better to the shaft.  This seems like something that I could easily screw up (I didn’t) and should have been taken care of at the factory.  I also failed to read information about the anti-backlash nuts until after I had assembled everything.  Oh well, there’s no going back now.
<p align="center">
  <img src="/images/posts/2012-12-28/assembled.jpg">
</p>
After assembly, I was confused.  How does one calibrate a CNC machine?  How does MeshCAM know where the cutting bit actually is on the wood to be cut?  Luckily, I stumbled across a post online and found out that because I ordered the USB option, I needed to download another piece of software called [Planet-CNC USB Software](http://www.planet-cnc.com/index.php?page=download).
<p align="center">
  <img src="/images/posts/2012-12-28/software.png">
</p>
Once I had this installed, things started to make more sense.  Planet CNC USB SoftwareUsing this software, I was able to move the X, Y, and Z axis motors to control the machine.  I was able to eventually open a .dxf (AutoCAD) file that I had saved from Adobe Illustrator in this software and convince the machine to make my drawing on a piece of paper with a pen.  This took several hours of work, and the process was certainly not easy.  Now I need to figure out how to incorporate MeshCAM into this process, and I need to find a proper CAD package to use.  Then I need to purchase some CNC bits to begin to cut some wood pieces.
<p align="center">
  <img src="/images/posts/2012-12-28/sign.jpg">
</p>
For two day’s worth of work, I’m at least impressed that something I made on the computer actually came out in the real world.  It is a very satisfying feeling!  Note, the tape in the image below was used to hold the paper to the board.  It was not mounted where it is shown, I had removed the piece of paper from under the machine for photo visibility reasons.  However, if I had turned the machine on without testing everything, I’m sure the machine would have tried to draw off of the main board.  My next move will be to attach some limit switches so it will keep the cutting head in a safe area on the main board.
