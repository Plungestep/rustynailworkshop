---
layout: post
title: Solar Powered Raspberry Pi
tags: [frontpage, electronics]
image: '/images/posts/2012-8-8/close_up.png'
---

When I first heard about the Raspberry Pi, a $35 computer that can run Linux, I was mildly impressed. My first problem was that I did not understand Linux, and my second problem was that I couldn’t figure out a need for a computer this inexpensive. Like all of my other projects, it was just a matter of time before I figured out that not only did I need to have this computer, but that I would find the perfect use for such a device.

Since I had missed the original order date for the Pi, I was either doomed to wait 10+ weeks for one to ship, or I would have to purchase one on E-bay. I debated going with a Gumstix computer instead, but finally settled on an unopened Pi being sold on E-bay. A few days later, I had a Pi to play with.
<p align="center">
  <img src="/images/posts/2012-8-8/sticker.jpg">
</p>
I had planned to use the Pi to feed some energy usage data to a web page, preferably hosted on the Pi, so that other devices and computers could connect to the Pi to see how much energy we were consuming. After learning some PHP and setting up an iWeb site, I was able to configure the Pi to run Apache and serve up the data I wanted. I’ll write more about this in a later post.

Because I like to do things the hard way, and I wanted to minimize the power consumption, I decided to set up the Pi to run off of solar power. After much research, I settled on a [50 watt solar panel](https://www.amazon.com/gp/product/B002OSAB28) sold by Amazon. The solar panel came with MC4 connectors on the back, and I was advised not to cut them off or I would void the panel’s warranty. So I also picked up a 12 meter MC4 solar panel cable.
<p align="center">
  <img src="/images/posts/2012-8-8/pi.jpg">
</p>
To store the power from the solar panel, I originally wanted to use some ultra capacitors. I found a few [3,000 Farad](https://www.digikey.com/en/products/detail/BCAP3000%20P270%20K04/1182-1021-ND/3079285) (yes, that is 3,000 Farads!) capacitors at 2.7 volts from Digikey, but at about $75 a piece, it would take too many to store the power I needed to run my Pi. Plus, I didn’t want to die and these things can dump a lot of power very quickly. So my next stop was at [Batteryspace.com](https://www.batteryspace.com).

At Batteryspace, I picked up a [LiFePO4 Prismatic Battery](https://www.batteryspace.com/lifepo4-prismatic-battery-12-8v-20ah-256wh-10c-rate-24-0---un38-3-passed-dgr.aspx) that was 12.8V and 20Ah. I also picked up a [PWM solar charge controller](https://www.batteryspace.com/Charge-Controller-120W-12V/24V-Auto-Detection-10A-Rate-for-SLA-or-LFP.aspx) to connect the solar panel to the battery and charge it correctly. Batteryspace recommended this combination to me specifically for the long life of the battery and the fact that it’s Lithium based, so the size is smaller than a deep cycle lead-acid battery.

I also needed a way to convert the 12 volts from the battery down to 5 volts for the Raspberry Pi. A quick trip to Target and I found a Griffin PowerJolt dual auto adapter that was designed to fit in a cigarette lighter plug in a car. I paid $16 at Target for this, but Amazon has it for $5.99.

I mounted the battery charger on the side of the battery, and connected the solar panel cable to it after cutting one of the ends off of each cable. I plugged in the solar panel, added some wires to the Griffin USB charger, and plugged in my Pi. It worked perfectly. I measure the total power consumption of my (wireless) Pi at 180 mA (average) and this includes both the consumption of the battery charger (6 mA) and the Griffin USB charger (5 mA).
<p align="center">
  <img src="/images/posts/2012-8-8/setup.jpg">
</p>
A quick calculation shows that a 20 Ah battery powering a device drawing 0.180 Amps will run for approximately 111 hours, or 4.6 days. Since the Pi does not draw a constant 180 mA, the real world run-time for this will likely be a lot less, but this doesn’t factor in the power the sun provides during daylight hours. I haven’t tested it yet, but I expect the solar panel will have enough power to run the Pi and charge the battery back up at the same time.

The total cost for this project was as follows:

* 50 watt solar panel: $158.95
* Solar panel cable: $28.95
* LiFePO4 battery: $124.00
* PWM charge controller: $27.95
* Griffin PowerJolt dual USB charger: $16.00

Total cost: $355.85

#### December 29, 2012 Update: 
The solar panel is the perfect size for the Raspberry Pi when the Pi is left running 24 hours a day, 7 days a week.  There are other solar powered Pi computers out there which are lower in cost, but I am almost positive those smaller solar panels would NOT be able to run the Pi continuously without human intervention.  My Pi has run since August with only one interruption.  I had one time the Pi shut off at the beginning of November when we experienced about seven days of cloudy conditions with no sun.  Since we are located in Minneapolis, Minnesota (USA), this means we usually have only about nine hours of daylight each day at that time of the year.  Since the charge controller indicates that the battery is charging even when it is cloudy outside (and thus the Pi is still running off of solar power during the daylight hours), my guess is that the charge being stored during the day was not enough to make up for the charge lost during the other 15 hours of darkness at night.  Thus, seven cloudy days finally drained the battery enough for the battery circuit to shut off the power (to protect the battery).  Once we started getting more sun, the Pi was back up and running continuously.  Yes, this setup is expensive, but this setup will power the Pi as a dedicated 24-hour-a-day web server.

#### January 24, 2013 Update:
I have now added a current sensor to monitor how the solar panel is charging the battery and how much power the Raspberry Pi is consuming.  The solar panel is putting out over 2 amps during peak periods of sun!

#### March 19, 2013 Update:
The Pi and solar panel have worked perfectly all winter.  I have not had any further outages the entire winter, even when snow accumulated on the solar panel.  The sun usually melts the snow quickly, or it sublimates and the panel is clear in a day or so.  The current sensor is working well and you can see spikes during the day when the clouds pass over the sun and decrease the panel output.

#### August 17, 2013 Update:
Still running after a year!  I noticed yesterday that the batter was completely full at 3:00 PM, so it is clear the solar panel is putting out more than enough power to bring it back to a full charge during the long summer days.  The Pi that I’m using is encased in a plastic Pi box from Adafruit, and the only maintenance I’m doing now is to blow the dust off every few months.

#### December 20, 2013 Update:
I noticed the Pi had drained the LiFePO4 battery again because we had almost a full month of cloudy weather.  Of course, it being the month with the lowest number of sunlight hours doesn’t help.  The charge controller starts blinking when the battery is too low to power the Pi, and I believe it shuts off power so as not to damage the battery.  No worries though, the Pi is still set to power up on its own when the batter has been sufficiently charged and is capable of supplying power to the Pi.  I normally just wait a day or so and the Pi will be back running again.  I’ve swapped out the Pi’s SD card a few times because my needs have changed.  Now this is only supplying weather data to the Weather Underground.

#### January 25, 2021 Update:
This device is still running.  The panel is still producing power and the battery has enough storage to still power a Raspberry Pi computer.  Of course, the Pi computers have gotten more efficient, but this is still a good long-term project.
