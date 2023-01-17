---
layout: post
title: Crock-Pot Yogurt Controller
tags: [frontpage, electronics]
image: '/images/posts/2012-5-20/controller.jpg'
---

About a year ago, a friend mentioned how she made yogurt in a Crock-Pot slow cooker. It sounded impressive, and a good way to save on the cost of yogurt. We also figured that we could customize our yogurt recipe and eventually make something that would rival the taste of store-bought yogurt.

After researching a number of ways to make yogurt in a slow cooker, it all essentially came down to heating some milk up to about ~180 degrees fahrenheit, then cooling it down and holding it at approximately 110 degrees for six to eight hours. Since I have some experience working with [Arduino](http://www.arduino.cc/) microcontrollers, I figured this was a natural project to take to the next level. I also had some experience with [PID control theory](http://en.wikipedia.org/wiki/PID_controller), so I knew I could write some software that would control a slow cooker and hit a desired set point with minimal error.

After some further research, I found Aaron Stubbendieck’s web site “[over-engineered](http://www.over-engineered.com/projects/sous-vide-pid-controller/#more-69).” On his site, he decided to use PID control theory to control a Crock-Pot so he could try sous vide cooking. After looking over his site, I was very impressed. Not only did he use an Arduino Pro Mini for his controller, but he also fabricated some circuit boards and used laser-cut acrylic for an enclosure. My project suddenly become even more attractive since I could learn to make my own circuit boards and enclosures!

I ended up using most of Aaron’s Arduino code, but revised some of his programming (so I could better understand it – it was a little complex for my skill level). I ended up adding a “Yogurt” mode and made it the default mode so that my controller would start on this mode when first powered on. I also added a buzzer to allow notifications to the user. You can download my code [here](/files/Yogurt_Maker.ino).

To make the circuit boards, I started with the Eagle files that Aaron provided, and modified them to match the circuit I wanted. [Eagle](https://www.autodesk.com/products/eagle/overview?plc=F360&term=1-YEAR&support=ADVANCED&quantity=1) is a free printed circuit board (PCB) design software package, and is fairly easy to use. I have attached my files, so you can download the schematics and layouts.

* Main circuit board [schematic](/files/main_schematic.sch)
* Main circuit board [layout](/files/main_layout.brd.zip)
* Button circuit board [schematic](/files/button_schematic.sch)
* Button circuit board [layout](/files/button_layout.brd.zip)

To make the circuit boards, I used BatchPCB.com, a circuit board aggregation service which collects a number of individual boards, groups them together, then sends them out to be made. The main circuit board cost $31, and the button board cost $14.43 to make. They did take several weeks to arrive, but I also received two of each board even though I had ordered only one of each. The work was flawless, including the printing on the boards. I was very impressed.
<p align="center">
  <img src="/images/posts/2012-5-20/circuit_boards1.jpg">
</p>

<p align="center">
  <img src="/images/posts/2012-5-20/circuit_boards2.jpg">
</p>
Aaron had used Adobe Illustrator to design the enclosure.
<p align="center">
  <img src="/images/posts/2012-5-20/design.jpg">
</p>
The service he used to laser cut the acrylic was [Ponoko](https://www.ponoko.com). I also used Illustrator (CS5.5) and waited until Ponoko had a sale. I submitted my [box design](/files/Enclosure.ai), and received my laser cut acrylic within a few weeks. I believe the cost was about $40, which included the cost of the acrylic. The acrylic arrived with a brown paper attached to it that you need to peel off. This protects the acrylic from scratches while you are working with it. I highly recommend the acrylic that has a matte finish on one side (the outside of my project) since it doesn’t show fingerprints. Ponoko did a fantastic job, and I would highly recommend them for future projects.
<p align="center">
  <img src="/images/posts/2012-5-20/laser_cut.jpg">
</p>
The pieces are easy to pop out from the acrylic sheet, and I glued them into place with some acrylic cement. Of course, I had to test fit everything first to make sure my measurements were accurate when designing the enclosure.
<p align="center">
  <img src="/images/posts/2012-5-20/test_fit.jpg">
</p>
For the temperature probe, I ended up using an audio jack and some very flexible audio cable. I put the one-wire temperature sensor in a [thermowell](https://www.brewershardware.com/Thermowells/) from Brewer’s Hardware. They were also easy to work with, I just emailed them my project requirements and they helped me select the appropriate sized thermowell.

After running into a few problems making the circuit work, I found out that resistor R4 on the main circuit board should be ~240 ohms, not 1K. When I had it set at 1K ohms, there was insufficient power to drive the optoisolator LED. Thus, the triac never turned on and I kept getting a very strange output.
<p align="center">
  <img src="/images/posts/2012-5-20/test.jpg">
</p>
My yogurt controller is set to heat the Crock-Pot slow cooker up to 178 degrees (which is as hot as my slow cooker goes in two to three hours), then it sounds an alert tone, and cools the yogurt down to 110 degrees. It holds the yogurt at that temperature until you unplug the controller. Since I also left in Aaron’s code for sous vide cooking, I can use this controller for other cooking as well. Never before has a Crock-Pot been so versatile!

Many thanks to Aaron for his work on this project. His web site taught me quite a bit and allowed me to make my own circuit boards and enclosure. After all, most of the fun in a project like this is learning to do something new. Now if you will excuse me, I’m off to eat some yogurt!
<p align="center">
  <img src="/images/posts/2012-5-20/final.jpg">
</p>
This is the final yogurt controller in operation.
