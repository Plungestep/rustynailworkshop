---
layout: post
title: Super PID Router Speed Controller
tags: [frontpage, electronics]
image: '/images/posts/2013-7-7/box.JPG'
---

After setting up the [Probotix Fireball V90 CNC machine](http://www.rustynailworkshop.com/archives/203), and using it to cut out a number of pieces for various projects, I decided I wanted a better way to control the router’s spindle speed.  Although the Bosch Colt router that I was using had a speed dial, it was impractical to adjust it as I was cutting a project, and impossible to tell what speed it was actually running at.  A setting of “7” on a 1-10 dial means nothing in terms of actual spindle RPM.

After discussing this with another CNC expert, I was pointed towards a [Super PID Speed Controller](http://www.vhipe.com/product-private/SuperPID.htm) from Vhipe (thanks Marv!).  The controller looks very well made, but unfortunately does not come with an enclosure.  This is a catch 22 issue.  How do you make your own enclosure with your CNC machine if you can’t control the speed, and how can you use the speed controller without an enclosure?  So I eventually set the router on maximum speed and cut out a custom bamboo enclosure for the speed controller.

The controller includes a sensor which you can mount in the housing of the router.  After some careful placement, I had a fully functioning speed controller, which appears accurate down to a single RPM.  I added a main power switch, a switch to turn the router on and off, and a switch to override the PID sensor control in case the sensor is clogged with dust.
![Controller Case](/images/posts/2013-7-7/controller.jpg)
When I constructed the box, rather than hard wire everything in place, I added a socket for the AC power cord, and a plug for the router’s power cord.  This will let me change routers without too much difficulty (with the removal of the sensor), and allow me to move the box if I decide it would look nicer next to a different outlet.  A clear cover let me see into the box to view the LCD display without having to machine an opening and deal with precise mounting of the circuit board.  Finally, a nice black metal knob on the potentiometer for the speed setting rounded things off nicely.

Now that I can control my CNC machine’s speed, the options are limitless!
