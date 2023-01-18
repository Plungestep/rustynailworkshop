---
layout: post
title: Fish Feeding Tracker
tags: [frontpage, electronics]
image: '/images/posts/2017-10-21/tracker.jpg'
---

If you have a fish tank, you know how important it is to remember to feed your fish.  Often in our busy, hectic lifestyles, we can forget to do simple tasks, such as dropping in a few flakes or pellets of fish food to take care of our pet fish.  It often isn’t intentional, but can easily happen due to oversight.  Compounding this problem in households with multiple people is the question of whether someone else has fed the fish that day.  If you add in small children, it is easy to overfeed a pet fish.  The solution to these issues is a simple Fish Feeding Tracker!

Designing and building a device to track the feeding of a fish is a relatively easy task.  We set out to make a device that was capable of the following functions:

* It must know the current date and time, and have a clear indication of whether the fish has been fed that particular day;
* It should have the ability to notify someone if the fish has not been fed by a specific time;
* Multiple reminders of a missed feeding would be helpful in case the first reminder is missed;
* It should be simple to operate for adults and children; and
* A camera to see the fish tank remotely is an optional, but nice feature.

The device chosen to implement this task was a Raspberry Pi 3, Model B.  Using the Raspbian Linux operating system and Python, a simple script can be written to accomplish all of the above objectives.  The Raspberry Pi can also host a web server and allows a camera to be connected, which enables remote viewing of the fish tank.  Finally, a custom enclosure can be made from acrylic, which keeps the Raspberry Pi safe from accidental water spills near the fish tank.

A [16 x 4 character LCD display](https://www.adafruit.com/product/498) can be used to show the feeding status, and if one is selected with an RGB backlight, the color of the LCD can also be chosen to visually indicate the feeding status from a distance.  In our case, a red display indicates the fish has not been fed that day, while a green display indicates a feeding has occurred.
![Red Display](/images/posts/2017-10-21/red.jpg)
To record that the fish has been fed that day, a simple [normally-open pushbutton switch](https://www.adafruit.com/product/3425) can be used.  When the switch is pressed (or closed), the Raspberry Pi can detect that a feeding has taken place, and log the date and time of the feeding.  To make the status even more evident, and to match the RGB background of the LCD display, an RGB-illumiated push-button switch can be used and programmed to match the color of the LCD display.  To those younger fish-feeders (children), this reinforces the fed or not-yet-fed status.  This makes it incredibly simple – just feed the fish and push the button.  It could also be taken a step further, to detect the lifting of the food container from a pressure-sensitive pad (or in the case of a fish food contain with a conductive-metal bottom, a conductive circuit could be used to sense the container removal).
![Green Display](/images/posts/2017-10-21/green.jpg)
The software chosen to allow remote viewing of the tank using a Raspberry Pi-compatible video camera was [RPi Cam Control](https://elinux.org/RPi-Cam-Web-Interface).  The nice thing about this software is that it allows customization.  You can add a username and password to be able to view the camera, and you can set operational times during the day.  The camera for this project was [a wide-angle Raspberry Pi camera](https://www.amazon.com/gp/product/B00N1YJKFS) that was mounted on a tall piece of acrylic sticking out of the top of the box, to position it closer to the center of the tank.  The distance from the Raspberry Pi was limited due to the camera’s cable length.
![Tank Camera](/images/posts/2017-10-21/camera.png)
I originally set up the code to send feeding reminders and status updates via a special email address using my cell phone number, which my cell phone carrier allows and then converts to a text message.  However, after my cell phone provider changed, the code was modified to simply send a regular email instead.  If the fish has not been fed by a specific time each day, a reminder email is sent.  Then two more reminders are sent, each a half hour later than the last.  Finally, as soon as the fish has been fed, an email is generated which indicates there was a successful feeding that day.  This is useful if children feed the fish when you are not available.

An acrylic enclosure was made with a modified box design from [makeabox.io](https://makeabox.io/).  Slots were added for the Raspberry Pi power cord, the camera cable and camera mount, and an access slot to remove the micro SD card for programming.  The acrylic was laser cut and glued together with acrylic cement.

The dates and times of the feedings are logged to the Raspberry Pi micro SD card so you can view the feeding status at a later date, if so inclined.

[Here](/files/fish_code.txt) is a copy of the code created for this project.  Enjoy, and make something fun!
