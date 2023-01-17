---
layout: post
title: Internet Controlled Robotic Arm
tags: [frontpage, experiment, electronics]
image: '/images/posts/2011-11-20/arm.png'
---

The motivating factor for the construction of this robotic arm originally came from a tour of the Volvo factory in Göteborg, Sweden. It was during this factory tour that I first saw the massive robotic arms used to pick up car parts and weld them on to the car body. With sparks flying, these were some of the most impressive robots I had ever seen, and if you ever have a chance, take the tour!

Fast forward one month, and I was the proud owner of my first robotic arm kit, a [Lynxmotion AL-5D](http://www.lynxmotion.com/c-130-al5d.aspx), with the heavy-duty wrist rotate mechanism. Oh boy did I have big plans for this arm!
<p align="center">
  <img src="/images/posts/2011-11-20/al5d.jpg">
</p>
Having some previous experience with Arduino boards, I immediately connected an [Arduino Uno](http://www.arduino.cc/en/Main/arduinoBoardUno) to the SSC-32 servo controller that came with the arm. With a little bit of web searching, I was able to find instructions and sample code which had me sending basic commands to each servo. It took another couple of weeks, but I had finally gotten the arm to move the way I wanted.

After trying to implement the inverse kinematics code written by Oleg from [Circuits at Home](https://www.circuitsathome.com), I quickly came to realize that supplying the arm with x, y, and z coordinates was not the most interesting or practical way to control it. Instead, I came across [Travis Smith’s internet controlled robotic arm](http://www.orbduino.com/index.htm). I had actually conceived of an internet-controlled arm shortly before I purchased it, and this was the evidence needed to convince me that an arm could be controlled over the internet.
<p align="center">
  <img src="/images/posts/2011-11-20/shield.jpg">
</p>
After waiting for an [Ethernet shield](http://www.arduino.cc/en/Main/ArduinoEthernetShield) to arrive, I proceeded to write some code that would receive individual commands in the the form of a URL string, translate those commands into an instruction for the SSC-32 servo controller, and thus move the arm in the intended manner. Using iWeb, I was able to set up a simple web site that allowed a user to click on the part of the arm that they wanted to move and watch it move by way of a video stream. The video stream is provided by an [Axis M1011 camera](https://www.amazon.com/gp/product/B001PEY9SE/ref=oh_o05_s00_i00_details). By the way, I highly recommend this camera, it is the best web-enabled camera I have ever used. No computer is needed, just an internet connection!

After the arm was functional, I continued to work out a few bugs where the Ethernet shield would crash if too many commands were received too fast. By allowing only one command every few seconds from the web site, this problem was eventually solved. I also added a laser pointer to help indicate the direction the arm was pointing, as well as a distance sensor (probably pulled from an automatic faucet), just for fun. The distance sensor is not linear, so I had to model the performance in a simple quadratic equation. It is fairly accurate now, although it still has limitations at far and very close distances.

I contemplated adding a second video camera to show the view from the top, but not only would this increase the project cost, this wouldn’t challenge the user as much. I wanted this to be a fun experience for the users, as well as a fun construction project on my end. I eventually added some simple code to prevent the arm from moving beyond some safe limits that I set, which prevented the user from pulling out the servo cables from the servo control board.
<p align="center">
  <img src="/images/posts/2011-11-20/switch.jpg">
</p>Because I am always concerned about power consumption with my projects, I added a PowerSwitch Tail II to allow the user to turn on the arm and desk light, which only powers the arm when being used and stops the servos from humming when the power is turned off. I set it to automatically power off after a period of inactivity, which is controlled by the software code. I also set the entire arm to power on only during my waking hours so that my family would not be annoyed by the noise from the constant movement of the arm.

To prevent users from trying to put the arm through the table or floor, I picked up the inverse kinematics code again and reviewed the articles written on the web regarding forward kinematics. This was much easier than the inverse kinematics derivation, and I was able to generate a forward kinematics equation to drop into my existing code. After some changes necessitated by the orientation and performance of my arm, the forward kinematics equation is able to prevent the user from putting the end of the gripper through the table. You can see the spreadsheet I created with the equation [here](/files/Forward.xlsx). You can download the Visio diagram I made [here](/files/Forward.vsd) (same as the picture below).
<p align="center">
  <img src="/images/posts/2011-11-20/kinematics.jpg">
</p>
The entire code for the Arduino board is available here. There are a number of improvements that I’d like to make to the arm, but that would only delay the release of the web site to the general public. I can’t wait to see what users can do with the arm!

This was a very rewarding project, and I hope you enjoy using it. As always, drop me a line if you have any questions or suggestions.
<p align="center">
  <img src="/images/posts/2011-11-20/offline.jpg">
</p>
I had a link for users to try out the arm, but due to excessive bandwidth consumption, I had to take it offline.  It was fun while it lasted!
