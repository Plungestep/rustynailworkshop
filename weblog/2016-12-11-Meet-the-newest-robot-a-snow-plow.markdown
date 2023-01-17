---
layout: post
title: Meet the newest robot - a snow plow!
tags: [frontpage, electronics]
image: '/images/posts/2016-12-11/snowbot.jpg'
---

After finding out that mowing a lawn in a rectangular pattern is quite difficult, I decided to spend some time perfecting our use of rotary encoders and the Piksi GPS by building a small robot that could plow the snow for me each winter.  A driveway offers a smooth, rectangular area to traverse, which should be fairly simple for a robot.  To start, I decided to construct a remote controlled snow plow with a first person view (FPV) camera.  Eventually, I will add the GPS and self-driving capability.  This robot was a blast to drive, especially sitting inside where it was warm while it was cold and snowing outside!

Rather than start with a self-designed chassis, I decided to go with a predesigned chassis from [SuperDroid Robots](http://superdroidrobots.com/).  The robot selected was a [IG52-DB4, 4-wheel drive all terrain heavy duty robot](http://www.superdroidrobots.com/shop/item.aspx/ig52-db4-4wd-all-terrain-heavy-duty-robot-platform/1648/) platform.  I customized the order with IG52-04 24VDC 136 RPM geared motors, with a bottom skid guard cover, a rear bumper, high grip tires, and an upper deck sensor mount.  The motor gearing later proved to be a good choice, and the robot can move at about 5 mph but still has significant torque to push heavy snow.
![Motors](/images/posts/2016-12-11/motors.jpg)
I was not very impressed with [SuperDroid Robots](https://www.superdroidrobots.com/).  While the parts themselves were well machined, their customer service left a lot to be desired.  Before placing an order, I contacted them several times to ask questions about their robot platforms.  Email responses were slow, and questions were answered poorly, and often incorrectly, on the phone.  Thankfully from our previous projects, I had some experience building robots of this type, so I knew what to expect.

Before assembly, I took the chassis parts to a local powder coating company for a nice paint job.  They did a wonderful job, but applied the wrong color.  I ended up liking the color they used, so I accepted it as it was.
![Chassis](/images/posts/2016-12-11/chassis.jpg)
Assembly of the platform was fairly straightforward for anyone with some basic mechanical skills.
![Chains](/images/posts/2016-12-11/chains.jpg)
Unfortunately, the instructions provided by SuperDroid Robots were almost completely useless, with many of the files they provided not being applicable to the platform I purchased.  I ended up resorting to YouTube videos and manufacturer data sheets, which gave me all of the information needed.  I also found numerous missing parts in my kit, parts which did not fit, and optional parts that I had ordered which clearly did not fit within the platform design.  Again, SuperDroid Robots’ customer service was less than helpful.  For example, I wish they would have told me the motor controller I selected from their options would not fit within the chassis as shown in their video.  It’s something I can work around, but requires additional design work on my end.
![Wheels](/images/posts/2016-12-11/wheels.jpg)
The upper sensor desk provides a lot of space to mount the electronics.  I used the upper level to mount the motor controller, switches, radio control (RC) receiver, a linear actuator to move the plow up and down, as well as the mounting bar for the lights and camera.
![Top of Snowbot](/images/posts/2016-12-11/deck.jpg)
To make sure I had complete control over this robot, I installed a Dimension Engineering picoswitch and separate emergency stop switch, both connected to a solenoid.  This means that in the event of an emergency, I can either hit the emergency stop switch on the top of the robot, or trip a switch on the RC transmitter and power to the robot’s motors will immediately be shut off.  One hopes never to have to use this, but I can attest to the need at least once during testing when the robot drove itself into a wall (oops!).  Luckily, no damage was done.

To control the plow blade, I used two linear actuators (6″ Stroke: 180 lb Thrust Linear Servo, part number [HDLS-6-30-12V](https://www.servocity.com/hdls-6-30-12v)) were purchased from [Servocity.com](https://www.servocity.com/).  Although Servocity’s prices were higher than I would have liked, these actuators worked perfectly and the construction quality was top notch.  I used one actuator to raise and lower the plow blade, and one actuator to turn the plow blade left and right so I could push snow off to the side.

The plow blade was manufactured by Nathanael at [Mill City Metal Works](http://www.millcitymetalworks.com/) out of 1″ aluminum tubing.  Nathanael was willing to tackle this project even with other metal fabrication shops turned down the work after deciding it was too difficult.  He quickly turned an abstract plow idea into a CAD file and then fabricated the plow in a few days.  Two hinges were used to allow the plow to raise and lower, and it was bolted onto the side of the lower robot deck next to the batteries.  Unfortunately, during one of the test runs, the plow blade caught on a crack and some of the aluminum welds snapped.  It should be easy to fix and will be back up and running before the next snow fall.

In order to control the snow plow from inside the house, [a small camera and 1.3 MHz transmitter](https://www.readymaderc.com/store/index.php?main_page=index&cPath=4_319) (used with an amateur radio license) was installed.  Inside, a pair of FPV goggles was used with a video receiver to allow the operator to see what the plow camera saw.  This turned out better than expected, and it was quite easy to drive the plow in this manner.

In the future, I plan to add a GPS and magnetic compass sensor to allow self-driving operation.  I also hope to use the motor encoders to make sure wheel slip is detected, which is common in the snow.
![Snobot Video](/images/posts/2016-12-11/snowbot_video.mp4)
Finally, here is a video of the plow in action. I tossed a towel over the electronics in this video to protect them until a permanent cover can be added.  Enjoy!
