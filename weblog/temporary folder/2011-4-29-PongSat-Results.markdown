---
layout: post
title: PongSat Results
tags: [frontpage, experiment, electronics]
image: '/images/posts/2011-4-29/balls.jpg'
---

Our PongSat ping pong ball was successfully flown on JP Aerospace flight “Away 47” on April 9, 2011 (it is the experiment on the far left above). It reached a height of 85,549 feet before the balloon carrying the ping pong balls popped and the experiment fell back to Earth.
<p align="center">
  <img src="/images/posts/2011-4-29/setup.jpg">
</p>

<p align="center">
  <img src="/images/posts/2011-4-29/liftoff.jpg">
</p>

<p align="center">
  <img src="/images/posts/2011-4-29/balloon.jpg">
</p>
The structure holding the PongSat balls as they went to the edge of space!

The weight of the balloon and payload was approximately 12.5 pounds, and it climbed at an average rate of 1,300 feet per minute. The flight duration was 1 hour, 25 minutes. JP Aerospace recorded a minimum temperature of -74.4 degrees Fahrenheit. The payload was recovered 27.25 miles from the launch site, which was near Pyramid Lake, Nevada.
<p align="center">
  <img src="/images/posts/2011-4-29/lake.jpg">
</p>
The two other launch vehicles used by JP Aerospace achieved heights of 101,722 and 102,949 feet respectively. We were a little disappointed our experiment did not exceed 100,000 feet, but for a free experience, we are extremely grateful for the opportunity provided by this organization.

Our PongSat ball.We waited about two weeks after the flight for them to sort, organize, prepare photos and videos, and eventually package everything up and ship our PongSat back to us. During this time, we had no idea whether they had followed our instructions and turned on the PongSat before the flight (or turned it off at the end). We had tried to plan for failure modes, such as forgetting to turn the device off (it was supposed so sit there and do nothing for 49 days or until the battery ran out), but we couldn’t plan for someone forgetting to turn it on before the launch.
<p align="center">
  <img src="/images/posts/2011-4-29/recovered.jpg">
</p>
When it arrived, we inspected it and immediately noticed that the ping pong ball was discolored. It had faded significantly, and the writing wasn’t as sharp as before it left. Underneath the metal and duct tape, the ball was perfectly white and new looking. We suspected that this was because of the intense UV radiation at the edge of space. In any event, the sensor was still in place, and the ball looked intact, which was a good thing.
<p align="center">
  <img src="/images/posts/2011-4-29/unpacked.jpg">
</p>
We disassembled the ball, the switch was in the off position and everything inside looked intact and all wiring was still connected. Another good sign! We disconnected the battery and connected it to the computer to dump the Arduino’s EEPROM memory. We held our breath and waited for data to appear.

After the initial program sequence, the screen filled with numbers – we had data!!! Now, a quick scan would tell us if they turned it on too early, or at the right time (just before the launch). It was only supposed to take data for three hours, so we were hoping it wasn’t data from the Nevada desert. Whew! A quick read told us we definitely had recorded some negative temperature values. It looked like we had realistic data!

Eventually, I plotted the data for the kids to analyze using Microsoft Excel. I highlighted the minimum and maximum temperatures to see the extreme conditions experienced. The two graphs obtained are included below.
<p align="center">
  <img src="/images/posts/2011-4-29/temperature.png">
</p>
The minimum temperature we recorded was -34 degrees Fahrenheit. The maximum temperature was 52 degrees, which seems logical for the early morning in the desert.
<p align="center">
  <img src="/images/posts/2011-4-29/humidity.png">
</p>
So what do these graphs mean? Was the experiment successful? The answer is a resounding YES! Although the data is different than what we expected, we certainly learned something from this flight.

Temperature: We expected this to be extremely cold, and were slightly surprised to see that the lowest temperature recorded was only -34 degrees. However, the STH-15 humidity and temperature sensor data sheet indicates the operating range for the temperature sensor is -40 to 249.5 degrees Fahrenheit. This means our sensor was in an error mode for a good portion of the flight. That explains the fact that we weren’t able to get to the -74.4 reading that JP Aerospace obtained. They used a mercury-type thermometer and observed the reading with a video camera.
<p align="center">
  <img src="/images/posts/2011-4-29/mercury.jpg">
</p>
However, you can clearly see the ascent and decent from the change in temperature. We also suspect the sunlight on the sensor caused a heating effect which kept the sensor at -34 degrees or even slightly warmer.

Humidity: We had no idea what to expect here, except that humidity in space was probably near zero. When we plotted this data, we clearly saw it go down to zero, but then it even went slightly negative. From reading the data sheet, a negative humidity reading indicates a sensor error. Since we were operating outside of the specifications for temperature, this makes sense that the sensor wasn’t operating correctly. However, the spike in humidity near 110 minutes may be due to the passing of the vehicle through a cloud. At least we like to think so. In any event, the starting humidity and ending humidity looks reasonable for a desert, so we suspect the humidity sensor operated correctly when the temperature was in the normal operating range.

The battery appeared to perform perfectly, even down to -74.4 degrees Fahrenheit. We are very impressed, and consider this experiment to be a wild success. Thank you JP Aerospace, you did an excellent job, even when the vehicle was upside down!
