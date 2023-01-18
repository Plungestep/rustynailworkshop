---
layout: post
title: Remote Temperature Sensor & Energy Monitor
tags: [frontpage, energy, sensors]
image: '/images/posts/2007-10-11/WEL.png'
---

Like any good do-it-yourself project, this one started with a need.  I have a home which has a radiant floor heating system.  I’ve never had a heating system of this type, and as such, I tried to learn everything I could about the operation of this system.  My biggest concern was the operation of the system when I wasn’t at home.  What if the house temperature dropped and the pipes froze?  How would I know?  Clearly I needed a way to monitor the performance of the system without actually being at home.

My first attempt started with a couple of temperature sensors located in a few rooms to monitor room temps.  Here’s where the problem suddenly became difficult.  Because I try to minimize energy consumption, I wanted a way to operate the temperature sensors without a computer running 24 hours a day.

Even with the most efficient computer, I’m still out $2,000 for the computer, plus the continuous cost of 10+ watts of power.  One example of a computer that can run under 10 watts is a Sony Vaio UX-280, but this is certainly not suitable for a long life web server.
<p align="center">
  <img src="/images/posts/2007-10-11/ux280.jpg">
</p>
I wanted to use the existing 802.11-g network in my house, and send the temperature data directly from the sensor to a web site.  Unfortunately, the only thing even remotely close to this was a temperature sensor from G2 Microsystems or Point Six.  Both are in the hundreds of dollars of cost per sensor!  Ouch.  I tried searching the internet numerous times for ethernet based temperature sensors, wireless temperature sensors, and even home monitoring temperature sensors – all without any luck.  Clearly I needed something else.  

> Update 7/19/09: You can now find a computer which uses three (yes, 3) watts of power.  Check out my other post about my Sony Vaio P, which has replaced the UX-280 I previously tried.)

Further research led me to a web site named [Our Cool House](http://www.ourcoolhouse.com).  Phil, the owner of this site, has designed and built a device called a Web Energy Logger (WEL).  
<p align="center">
  <img src="/images/posts/2007-10-11/WEL_board.jpg">
</p>
This device, which includes its own built-in web server (which is unfortunately not wireless – yet), costs about $350 and can monitor tens, if not over a hundred, sensors.  They can be temperature sensors, current sensors, and many others.  Although the device is a little expensive, it is apparent that Phil has put a lot of time into the design and software used by this device.  It functions both as a web server as well as a data logging device (but the data is stored at a remote web site [www.welserver.com](http://www.welserver.com).  The device uses a communication bus called 1-wire, which was original developed by Dallas Semiconductor for low-speed data signaling and power of a single wire.  The 1-wire name is a misnomer, the sensors actually use two wires, but only one wire carries the data and power for each sensor, the other wire is ground.  Knowledge about this sensor network really isn’t necessary to make this device work, but it is helpful for those looking to understand how it operates.

First, I needed to design my 1-wire network for the WEL to monitor.  I started by creating a list of locations where I wanted to monitor the temperature.  My list looked a little like the following:

1. Heat (Air) Exchanger
* Fresh Air In
* Stale Air In
* Stale Air Out
* Fresh Air Out
2. Water Temperatures
* House Hot Water
* House Cold Water
* Radiant Floor Water Heater
3. Room Temperatures
* Master Bedroom
* Living Room
* Kitchen
* Bedroom #1
* Bedroom #2
* Family Room
4. Miscellaneous  Temperature
* Outside
* Attic
* Utility Room Floor
* Garage

I purchased 18 temperature sensors (DS18B20-PAR) and I planed to solder them up myself.  
<p align="center">
  <img src="/images/posts/2007-10-11/DS18B20.jpg">
</p>
Although they have three leads, only two of them are used.  I also purchased several current sensors to monitor whether a motor or heater is running.  I plan to use my home’s existing telephone wiring, which all comes to a connection point in my garage.  Most telephones only use the two middle wires of the four installed in each jack, so I planned to use the two outside (and currently unused) wires.  Thus, there would be no need to run additional wires in my house.

My favorite part about the WEL device is the ability to overlay my temperature sensor readings on top of an image that I supply.  I immediately thought of [Google’s SketchUp](https://www.sketchup.com) software, which is free.  This allowed me to create a three dimensional view of my house.  I will overlay my sensor readings on top of this image with the tools provided on the WEL site.
<p align="center">
  <img src="/images/posts/2007-10-11/floor_plan.jpg">
</p>
All 18 of the temperature sensors arrived and I started to construct my sensor network.  After installing about three temperature sensors, I wished I had opted for the pre-soldered sensors from [www.welserver.com](http://www.welserver.com/).  This would have saved a considerable amount of time and frustration attempting to solder tiny connections, while making sure everything had enough heat shrink tubing over them to prevent short circuits.
<p align="center">
  <img src="/images/posts/2007-10-11/wired_sensor.jpg">
</p>
I tried to wire everything in a star configuration (one main twisted pair cable with multiple lines running outward from one central point), which was recommended when I purchased the WEL device.  Some sensors didn’t work well in this configuration, so there are a few branches on the main leg of my star network.

I connected the WEL to my router, and began testing and updating individual sensors.  Oddly enough, everything seems to be working.  No need to configure the WEL IP address or any other network configuration!  The sensors came online one at a time, just after I plugged them in.  Temperature data and run-time data began flowing immediately.  I couldn’t have asked for a better installation.
<p align="center">
  <img src="/images/posts/2007-10-11/mounted_WEL.jpg">
</p>
I went to the WEL web site that Phil supplies, and began to specify how I wanted my log file to look, and how I wanted my data displayed on my personal image (see house layout above).  I had some configuration to do here, but once I placed everything, it should be fairly permanent.

I expect to add more sensors in the future, now that I’m getting some good data.  This really surpassed my expectations!  Installation was a breeze, especially since I used the yellow/black wires from my already-installed telephone jacks.  The red/green wires supply my phone service, and the two exist peacefully next to each other.  I have to give this project a 10 out of a possible 10 point scale.  Way to go Phil, this is a great device!  It is obvious a lot of time and effort went into this product.

### Update (10/6/07)
<p align="center">
  <img src="/images/posts/2007-10-11/pipe.jpg">
</p>
My device has been working well now for several months.  I have found a couple of issues that Phil has been working hard to fix.  First, if you live in a very cold climate, like Minnesota, you will have scaling problems on the graphs when it gets down to -15 degrees or below.  Second, it appears that the longest history recorded is only about 12.5 weeks.  Thus, if you plan to record temperatures over a year, you may have to keep the data yourself.
<p align="center">
  <img src="/images/posts/2007-10-11/WEL_config.jpg">
</p>
The WEL server web site now has location information for the WEL devices installed world-wide.  It is kind of fun to see everyone who has purchased these and how they have put them to work.  Phil has also graciously added an alert function, to indicate things like a low temperature alarm.  Only one alarm is allowed, but it looks like Phil will offer more as premium services in the future (presumably for additional cost).

Overall, I’m still very impressed.  You can’t find a better internet based temperature monitor for your money.  This one just works.

### Update (7/19/09)
<p align="center">
  <img src="/images/posts/2007-10-11/wall_jack.jpg">
</p>
I’ve removed the device from my original home, and moved it to a new location.  Using the two unused wires on phone jacks made it very easy to remove and bring with me.  At the new location, it took only a few minutes to connect it to the existing phone wiring (not the active lines, of course) and I simply plugged in each sensor one-at-a-time.  When each one came online, I reconfigured the graphics on the WEL Sensor web site, and I instantly had a new setup.

A few months later, I had an air conditioner burn out.  We ended up with a new furnace and air conditioner.  The new furnace has a variable speed blower.  The installer, while giving us a sales pitch, told us to run the furnace blower on “low” all of the time to even out the temperatures in the rooms.  Oddly enough, the next day I read an article in the Star Tribune newspaper contradicting this advice!  Well, with a sensor in each room monitoring the temperature, I decided to test this out myself!

I let the system accumulate some data with the furnace fan set to “auto.”  After a few days, I turned the furnace fan to “low” which caused it to run continuously at a low speed all day long.  I found absolutely NO difference in the temperature readings between the levels in my house.  The newspaper article was right, and I can save money by not running my furnace continuously!
<p align="center">
  <img src="/images/posts/2007-10-11/bedroom_temp.jpg">
</p>
Phil has also taken the time to update the quality of the graphs at his site (see above), which makes it much easier to read the data.  I’m continually impressed by this system, it was well worth the purchase price.
