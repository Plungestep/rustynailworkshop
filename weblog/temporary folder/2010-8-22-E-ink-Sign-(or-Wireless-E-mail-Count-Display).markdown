---
layout: post
title: E-ink Sign (or Wireless E-mail Count Display)
tags: [frontpage, electronics]
image: '/images/posts/2010-8-22/sign.jpg'
---

After using the Arduino microprocessor board for the past year or so, there are often projects that pop into my head unexpectedly that would be perfect for the Arduino. One such project was a desire to display the number of e-mail messages I had received on some type of electronic sign, which happened to be away from my computer. Thus, I needed a wireless way to display information.

It was about this time that I found the [Google Radish project](https://developers.google.com/gdata/articles/radish?csw=1). For those that do not know, the Google Radish project was an attempt to display calendar data on conference room doors. The display updated automatically, and used solar power with a wireless connection back to a computer to pull the data. I figured I could replicate this in a slightly modified form with an Arduino.

First, I purchased an [Arduino Duemilanove](https://www.sparkfun.com/products/11021) from SparkFun. I’ve used this board in the past, and it is very easy to work with and the code is very easy to learn. I also needed a display for my data and a pair of radios to set up a wireless link. After much searching, I settled on a [240 x 160 Kent Display ChLCD screen](https://www.sparkfun.com/products/retired/95600). At almost $80, buying this display without much sample code was a big risk, but one I was willing to take. After all, great reward follows great risk – and buying electronics is hardly a big risk when you consider everything else in life.

In order to transmit my data from my computer to my Arduino board, I needed a pair of radios. The Google Radish project used 802.15.4 radios, otherwise known as Zigbee radios. As it turns out, SparkFun also sells these, under the brand name of XBee. I also found someone who used Bluetooth to transfer data from a computer, in a [project](https://blog.printf.net/articles/2010/03/30/email-counting-tshirt/) similar to what I wanted to do. However, since Bluetooth is prohibited where I work (and where I wanted to set up my display), I purchased an [XBee kit](https://www.sparkfun.com/products/15936), which contained two series 1 radios, both at 1 mW output with a chip antenna.
<p align="center">
  <img src="/images/posts/2010-8-22/module.jpg">
</p>
I didn’t want to get into antenna theory, and I knew that the distance I needed to cover was less than 80 feet, so the chip antenna was more than adequate.
<p align="center">
  <img src="/images/posts/2010-8-22/xbee.jpg">
</p>
In order to get my project working, I needed to start in stages. I knew nothing about wireless radios, and I knew even less about ChLCD displays. So I started with the radios. I found a cool piece of software from Shigeru Kobayashi called XBeeConfigTool (link no longer available). This tool let me set up my radios without having to learn a lot about Zigbee parameters. Once I had them both configured and set to the same baud rate, I started on my Arduino software to make the radios talk to each other. One radio was installed on an XBee shield on my Arduino board, and the other radio was connected to an XBee Explorer which was in turn connected to my computer with a USB cable. In the end, the two radios essentially made a serial link between each other and enabled the Arduino Serial Monitor to send commands which were received by the remote XBee/Arduino setup just as if it was connected by a cable to my computer (but it wasn’t). Once I was able to send numbers like “123” to the remote Arduino, I knew this part was done. Here’s a tip, make sure the XBee shield is set to “UART” and take the shield off when programming the Arduino board or it won’t upload correctly.
<p align="center">
  <img src="/images/posts/2010-8-22/screen.png">
</p>
Above: I used the Physical Pixel example sketch to test if I was sending data correctly using the XBee modules. When I sent an “L” the LED went off. When I sent an “H”, it went on. It worked!

Next, I needed to find a way to display data on the Kent display. This took a long time since it did not appear that anyone else had solved this problem, and source code certainly was not available which displayed text or images. Eventually I found a way to convert images to hex values, then uploaded those hex values to the display, and it worked! For more information, see my post about the Kent display. Getting a font to render was very, very difficult. In the end, I simply created images for large numbers (each 40 x 60 pixels) and stored those in PROGMEM in the Arduino. Then when I wanted to write the numbers, I called each one line by line, drawing a row across the screen. You can see that in my code, which I’ve linked to [here](/files/email_code_sample.pde).

Once I had the XBee modules and the display working, I purchased a [Pololu switch](https://www.pololu.com/product/751) so I could cut power to the Arduino with the software. These are cool switches, and if you haven’t used one, you really should try them out. Now I simply needed a way to power the circuit I made. Originally, I purchased a 2.5 Watt solar panel (about 7” x 5”). This produced 9V, but almost zero current, so it was a complete waste of time. I considered using a solar engine to charge a super capacitor, which would then power the Arduino for the 5-7 seconds I needed, but the solar panel was too weak to do this. (As a side note, I did prove that a 5F/5V capacitor can easily power the Arduino board and XBee shield for ~30 seconds or more, once fully charged.)

I eventually settled on batteries, but I needed a way to wake the Pololu switch up electronically once every 10 minutes or so. I stopped by my local Radio Shack and picked up a TLC555CP timer chip (a low power 555 timer). I wired this up as an astable timer, using a 470 uF capacitor, 1m Ohm resistor with a second 22k resistor. This produced a logic high pulse of about 6 minutes, with a logic low pulse of 7 seconds. The 7 seconds was all I needed to power the Arduino board to wake up, get the serial data (or number of e-mail messages), and then it would cut the power. It turns out that I ended up using the Pololu switch in a way they didn’t intend. When the logic low (0 volts) was applied to one side of the “switch” contacts on the Pololu switch, the switch turned on. When the 555 went high (5 volts), the switched automatically turned off. Thus, I was using it similar to a transistor to supply power to the entire Arduino/XBee boards with just a simple logic pulse. (There is probably a better way to do this, but it worked!) With no power to the Arduino/XBee boards, I was using only 0.1 mA of power from my batteries to run the 555 timer. Wow! With the Arduino/XBee boards running, I was using about 80-100 mA to refresh the screen (but only for 7 seconds at a time). If I turn this off at night, I estimate the batteries (2000 mAh) to last for 3.8 months. Perhaps I can use my solar cell after all (but that’s for another time).
555 Timer Circuit
<p align="center">
  <img src="/images/posts/2010-8-22/circuit.gif">
</p>
This is a diagram of the TLC555CP timer circuit that I used. R1 = 1m Ohm, R2 = 22k Ohms, and C = 470 uF.

I mounted the boards, batteries, and display on a piece of acrylic. I then wrote a small VBA script to run in Microsoft Outlook to count and write the number of e-mails I had received to a text file on my computer. I then wrote a small Python script to send the number from the text file out over the serial port (really a USB port) to the XBee module I had plugged into my computer. If you want to count the number of messages directly from Gmail, you can use this script. If you download this code, just change the extension to “.py” and it will work with Python. Once this was sent, my display would wake up, get the data, update the display, then go to sleep.

I’m sure a few of you will recognize that 846 is an unrealistic number of e-mail messages to receive. In the process of testing this, I randomly saved numbers to a text file to see if they would upload correctly. They did! (I also blurred out the background in the photo above since it contains some work-specific information.)

I’m sure I could optimize this further, but I already have about 50 hours into this project and I want to move on to the next project.

Oh, and here is my [Arduino source code](/files/email_code_sample.pde) if you would like to replicate this. It’s filled with comments, which should make your life easier than mine! I replaced my work-specific background with an image I used to test the display. You’ll want to include your own background image (in the form of a large hex array).

Enjoy!
