---
layout: post
title: PongSat Experiment
tags: [frontpage, experiment, electronics]
image: '/images/posts/2011-4-9/ball.jpg'
---

Today, our first [PongSat experiment](http://www.jpaerospace.com/pongsat/) will be launched to the edge of space! [JP Aerospace](http://www.jpaerospace.com), a group located in California, offers to fly student experiments that fit inside of a ping pong ball to the edge of space, often over 100,000 feet above the surface of the Earth. Did I mention that they do this at no cost to the experimenter? To get started, you only need to send an e-mail to [jpowell@jpaerospace.com](mailto:jpowell@jpaerospace.com).

With the help of my two boys, we created a ping pong ball experiment to measure the temperature and humidity over the course of the ascent and descent of the balloon used to carry the balls up to space.

Our PongSat was built in March of 2011. It contains an Arduino Pro Mini running an ATmega368 microprocessor at 8 MHz (0.5% tolerance). It is a 3.3 volt low voltage board weighing less than 2 grams. The total cost of this board (from [Sparkfun](https://www.sparkfun.com/products/11113)) was $18.95.
<p align="center">
  <img src="/images/posts/2011-4-9/cut_open.jpg">
</p>
The inside of our PongSat ball, ready to be assembled.The board is powered by a single 1/2 AA Lithium Thionyl Chloride 3.6 volt 1.2 Ah battery. Lithium Thionyl Chloride batteries have a unique property in that they will function in very cold conditions, down to -55 degrees Celsius. The battery cost us only three dollars.

Connected to the Arduino board is a Sensirion SHT15 digital CMOS humidity and temperature sensor. 512 temperature and 512 humidity values will be stored to the Arduino’s EEPROM memory over a course of three hours. The boys selected readings to be taken about every 21 seconds, so we should fill the available memory locations during the flight.

We wrapped as much of the ball in metal tape to try to deflect as many cosmic rays as possible. We weren’t sure what would happen if we didn’t protect it, but after looking at images of other satellites, we determined they covered the devices in a gold colored film. We used what we had on hand, which happened to be metal tape.

The source code for the Arduino board can be viewed (and used) [here](/files/PongSat_Code.pde). Feel free to use this for future experiments, and hopefully improve on what we have done.

To view the PongSat experiment results, please see my other post about the results.
