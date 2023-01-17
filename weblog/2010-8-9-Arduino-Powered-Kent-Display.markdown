---
layout: post
title: Arduino-Powered Kent Display
tags: [frontpage, electronics]
image: '/images/posts/2010-8-9/display.png'
---

While working on a project where I needed to display some data, I came across a cholesteric liquid crystal display (ChLCD) from [Kent Displays](https://kentdisplays.com), sold by SparkFun Electronics [](LCD-09560, 240 x 160)](https://www.sparkfun.com/products/retired/9560). The unique aspect about this display is that the image is persistent, meaning it has the ability to retain the image on the screen even when the display is no longer powered. This means the device can save power by shutting down the display until the next time an update is needed. The down side is that the display’s refresh time is on the order of two to three seconds. Therefore, it is not suitable for animated graphics, just static images.
<p align="center">
  <img src="/images/posts/2010-8-9/module.jpg">
</p>
After purchasing the display, I attempted to use the [sample code](http://www.sparkfun.com//Code/Kent_LCD_Large.zip) provided by SparkFun Electronics. With a minor modification, I was soon able to display alternating vertical bands of black and white bars which proved the display functioned correctly. Now I needed to display my own images.

Since I am using an [Arduino Duemilanove](https://www.sparkfun.com/products/11021) to control this display, I needed some custom code to upload images. After much reading, I found out the images are loaded to the display as a hexadecimal array, one hex value at a time. These hex values are stored in the display’s onboard image RAM (memory), and then a command is used to read the image RAM and update the screen. The memory for my particular display was large enough to hold three full screen images.
To generate an image, I needed to convert a monochrome bitmap (.bmp) file into the hex array. The image was created using Photoshop Elements, and saved as a bitmap file with one bit per pixel.
<p align="center">
  <img src="/images/posts/2010-8-9/alligator.jpg">
</p>
After two days of trying to make this image into the correct array and display on the screen, I realized I needed software to render the array by reading the image horizontally, not vertically. This means the Arduino KS0108 graphical LCD library would not work for my purposes. The KS0108 library contains a program to create arrays from monochrome bitmap images, but it only encodes vertically. In the end, I ended up using the software provided [here](http://en.radzio.dxp.pl/bitmap_converter/) to generate the hex array because it allows you to select the direction of encoding. I then simply cut and pasted only the hex values from the resulting array (after saving it to a text file) into my Arduino code. I stored the array in progmem because the array was very large. If you end up storing lots of full screen images in your code, make sure you are not facing memory issues with the Arduino.
<p align="center">
  <img src="/images/posts/2010-8-9/computer.jpg">
</p>
The code I used to display an image on this screen is included below. Please note, this code is not very clean, but it works. I’m sure someone else out there will take it and make it a lot more efficient and clean (feel free!).

Here is the .pde Arduino file: [Kent Display Sample Code](/files/Kent_Display_Sample.pde)

It will only generate a full screen image (for a 240 x 160 screen size) from the hex array included in the code. The hex array included is for the image shown above. If you are driving a larger sized screen, you will need to update the image array (with a larger sized image) and the following line in the code to indicate the byte size of your array (my byte size was 4800, which is also shown on the Kent Display data sheet for this display).

    for(int j = 0x00; j < 0x12C0; j++){

In this line, the “0x12C0” equals 4800 in hex, which is the last byte in my display. If you purchase the larger display, you will need to update this to read the hex value for your last byte. The display turns each hex value into a binary value, then displays dark and light pixels based on the binary ones and zeros. Thus, each hex value is turned into eight pixels, starting with the upper left of the screen and ending in the lower right. 240 x 160 = 38,400 pixels. If you divide this by eight (eight pixels per byte), then you get 4,800 bytes.

Finally, here’s an image to prove I could write to it!
<p align="center">
  <img src="/images/posts/2010-8-9/working_display.jpg">
</p>
Now, take this information and make something useful out of it. Then make sure you tell everyone so we can continue to make neat things!
