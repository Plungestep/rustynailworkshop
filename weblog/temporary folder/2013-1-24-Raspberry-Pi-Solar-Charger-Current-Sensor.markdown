---
layout: post
title: Raspberry Pi Solar Charger Current Sensor
tags: [frontpage, electronics]
image: '/images/posts/2013-1-24/charger.jpg'
---

After constructing a solar panel and battery system to power a Raspberry Pi, I wanted to find a way to monitor how the battery and charger was performing.  There are several ways to accomplish this task, usually involving a voltage sensor, a current sensor, or both.
<p align="center">
  <img src="/images/posts/2013-1-24/schematic.jpg">
</p>
A voltage-based sensor can be used to monitor the charge of the battery.  Over a typical day, the battery voltage should rise as the solar panel charges the battery, and then discharge at night while the Raspberry Pi consumes power from the battery.  A common technique for monitoring voltage is to use a voltage divider.  If appropriate resistances are chosen for the voltage divider circuit, the drain on the battery from the sensor is negligable.

Another option is to use a current sensor.  A current sensor placed off of one of the battery terminals will measure how much current is flowing into or out of the battery.  If you would prefer it in terms of power, the power being supplied or consumed from the battery can then be calculated using the following equation:

P = I x V

where:

* **P** is the instantaneous power, measured in watts;
* **V** is the potential, or voltage, measured in volts; and
* **I** is the current, measured in amperes (a.k.a amps).

I chose an Allegro MicroSystems ACS712 current sensor, which can be found on eBay for $2 – $4 each.  The one I selected was rated for +/- 5 amps.  Rather than use batteries or another wall adapter to power the current sensor, I chose to connect it to the Raspberry Pi using an [Adafruit Pi Cobbler](http://learn.adafruit.com/adafruit-pi-cobbler-kit/overview) cable.  Adafruit also sells several prototyping circuit boards, and I purchased one so I could mount the cable, analog to digital converter, several resistors, and the current sensor.  The [one I happened to purchase](http://www.adafruit.com/products/723) was sized to fit in an empty mint tin (more Altoids, anyone?).
<p align="center">
  <img src="/images/posts/2013-1-24/breadboard.jpg">
</p>
My first step was to assemble the Adafruit Pi Cobbler.  The instructions provided by Adafruit were excellent, as usual and I had no trouble with this assembly.  Since the Raspberry Pi uses a digital input, I needed to convert the analog sensor value into a digital value.  For this, I chose the [MCP3008 chip](https://www.adafruit.com/products/856), also provided by Adafruit.  In short order, I had the Raspberry Pi sensing the resistance changes by using a potentiometer as a simulated analog value.  To get the Raspberry Pi to sense the input, I had to install some software on the Pi.  I followed the instructions from [this Adafruit site](http://learn.adafruit.com/reading-a-analog-in-and-controlling-audio-volume-with-the-raspberry-pi/necessary-packages), but did not install alsa-utils or mpg321 since I’m not using the Rapsberry Pi to control the volume as the tutorial explains.  I also had to run “sudo apt-get update” first before installing python for it to install correctly.

Quickly I found I had another problem.  “easy_install” was not found on my Pi, but was required by the setup instructions.  I found that I needed to run “sudo apt-get install python-setuptools” to get “easy_install.”  (By the way, I submitted this as a suggested improvement to Adafruit, and they updated their web site within about 24 hours – impressive!)  I then copied the sample code from Adafruit, pasted it into a text file and renamed it readsensor.py.  I then used [Cyberduck](http://cyberduck.ch/) to SFTP it to a new directory I created on my Pi.  I made it executable while viewing that directory by running:

    sudo chmod +x readsensor.py

<p align="center">
  <img src="/images/posts/2013-1-24/python.png">
</p>
The next step was simply to replace the potentiometer with the current sensor.  Unfortunately, it is not as simple as just swapping out the potentiometer for the current sensor.  The Raspberry Pi uses 3.3 volts DC and the ACS712 current sensor uses 5 volts DC.  I needed a way to convert the 5 volt output of the current sensor down to something with a maximum of 3.3 volts.  The solution to this was very simple.  I used a voltage divider.  A quick check online told me that I should use roughly a 51k resistor and a 100k resistor for 5 volts DC in and 3.3 volts DC out.  After digging through the Rusty Nail Workshop parts bins, I was able to find some suitable resistors that were close enough to these values.  A quick check on the breadboard showed I had 3.315 volts out.  Perfect.
<p align="center">
  <img src="/images/posts/2013-1-24/cobbler.jpg">
</p>
After soldering everything up to the prototyping circuit board, I connected the voltage reference pin of the analog to digital converter to the Raspberry Pi’s 3.3 volt DC supply.  I then measured the open circuit current (which was zero since nothing was connected to the current sensor) and found the voltage output was exactly half of the 3.3 volt maximum needed by the Raspberry Pi.  The voltage divider was working perfectly.

A few more tweaks here and there and I had the Pi collecting current sensor data.  I found I needed to create an adjustment factor to help calibrate the current sensor.  It was reasonably accurate when the current was around 150 mA, which was suitable for my purposes.  To make sure I eliminated as many errors as possible, I set up some code to average some sensor readings.  If you would like to use my Python code, feel free to download it [here](/files/readsensor.txt).  Just remember to rename it with a .py extension so it will act as a python script.

I wanted to collect the current sensor data so I could see trends over time.  An instantaneous reading is nice, but I wanted to make sure current (or power) was flowing into the battery during the day.  Better yet, I wanted to know how much current was flowing in during the daylight hours.  Was the battery charging a little or a lot?
<p align="center">
  <img src="/images/posts/2013-1-24/pip.png">
</p>
[Cosm.com](https://cosm.com/) allows you to upload sensor data (for free!) and will graph it for you.  To get started, I found a tutorial on uploading data from Adafruit (where else?).  Of course, the tutorial was excellent.  (Notice a pattern here?)  I did have a problem since I did not have eeml installed on my Pi, so I had to run “sudo git clone git://github.com/petervizi/python-eeml.git”.  I then changed directories to the eeml folder by typing “cd python-eeml/” and I installed it by typing “sudo python setup.py install”.  After receiving another error about missing lxml, I realized I should have run “sudo apt-get install python-lxml” before installing eeml.

After everything was installed, and the software was appropriately edited with my Cosm key and id, I had data uploading and visible on the web site!

The last step was to make the python script run when the Raspberry Pi booted.  For this step, a Google search led me back to Adafruit (by now I should have just skipped Google and gone their as my first step).  Using the instructions [here](http://learn.adafruit.com/drive-a-16x2-lcd-directly-with-a-raspberry-pi/init-script), I was able to make the script boot on startup.  You can download the script I used [here](/files/sensor.txt).  I did notice that the sensor stopped uploading after about 10 minutes, so as an experiment, I set up a crontab job to start the service every five minutes.  This way, at the most, I’d only lose about five minutes of data if the service suddenly stopped.  I later determined that although this was a potential solution, this wasn’t a good solution, so I modified the python script to simply take one reading every 30 seconds.  I then caused it to ignore any errors uploading to Cosm, so hopefully this will solve the problem where the script stops responding.

After letting it run for a day, I was surprised to see over 2 amps of current flowing in during the peak daylight hours.  During the evening hours when the sun had gone down, I saw a current draw of approximately 171 mA.  I used a multimeter to verify the current consumption and then corrected my adjustment factor in the software to make the data match the multimeter.  As a secondary data point, a quick check on the solar panel specifications indicates that a little over 2 amps is the maximum current the panel will produce, so it is in the right ballpark!  Now I just need to add a voltage divider to measure the battery voltage.  I also found out later that adding an amplifier may give me better resolution for low current sensing.  That’s a future project.

There you have it!  A Raspberry Pi which is solar powered, runs 24 hours a day, 365 days a year AND which provides some energy data from a Web Energy Logger to me as a web server, uploads weather data from a Davis Vantage Pro weather station, and monitors its own solar panel/battery performance while uploading data to Cosm.
