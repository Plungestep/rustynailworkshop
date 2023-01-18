---
layout: post
title: Do-It-Yourself Blu-Ray Laser Pointer (Part 1)
tags: [frontpage, electronics, experiment]
image: '/images/posts/2009-3-7/bd_player.jpg'
---

About six months ago, I purchased a [Sharp Aquos BDHP20 Blu-Ray player](https://www.amazon.com/Sharp-Aquos-BDHP20U-Blu-Ray-Player/dp/B000W8SSXQ) to watch movies I rent via [Netflix](http://www.netflix.com/).  The DVD player worked perfectly for several months, enabling me to watch all sorts of movies in high definition.  Life was good.

Then one day, a disc refused to load.  I figured it had a scratch, and I tried other Blu-Ray discs.  None would load.  I found a firmware update, and updated the firmware.  No go.  The player still wouldn’t read the discs.  It played DVDs just fine, but not Blu-Ray discs.  I eventually got frustrated enough to purchase a new Blu-Ray player, figuring I’d dissect the old player and extract the Blu-Ray laser diode.

Some history is in order here.  I built my first laser pointer in 1991, from a schematic provided by a Popular Electronics magazine.  The red laser diode cost me $150, direct from Toshiba.  I still have it, and the laser pointer, although big, works perfectly.

With my two boys, I took the cover off of the Blu-Ray player and started to track down the laser diode assembly.  Very quickly, I found a box that looked like an external DVD player that you might find for your computer.

I removed the assembly that accepted the discs simply by unscrewing a few screws and pulling out a few cables.  This process was very similar to removing a CD drive from a desktop computer.  In fact, some of the connectors looked exactly the same.
<p align="center">
  <img src="/images/posts/2009-3-7/drive.jpg">
</p>
Disassembling this drive took a little more work since the cover had some metal tabs that needed to be unbent before the cover would come off.  I cut my thumb in the process, so please be careful if you try this at home.
<p align="center">
  <img src="/images/posts/2009-3-7/case_off.jpg">
</p>
The photo above shows the inside of the drive assembly.  The black circle in the middle of the above photo is the part that spins the disc in the drive.  The entire center assembly moves forward and backward on a threaded rod so the laser can read from the center to the outer edge of the disc.
<p align="center">
  <img src="/images/posts/2009-3-7/sled.jpg">
</p>
After a few minutes, I found the screws that allowed me to remove the laser assembly.  You can also see the threaded rod better in the above photo.  I just cut the ribbon connectors and pulled this out since I’m not going to be using the connectors anyway.  I’m after the laser diode itself.
<p align="center">
  <img src="/images/posts/2009-3-7/ribbon.jpg">
</p>
I finally removed the mechanical pieces and pulled out the optical assembly (as shown above).  This piece easily fits in the palm of your hand, and houses what appears to be two lenses, several tiny glass mirrors, and some tiny electronics.  The lenses are on a moveable section held in place by very fine wires.  I originally thought this was what I wanted to extract.  I was wrong, as I later found out.  There are small coils of wire and strong magnets under the lenses that are used to focus the light beam on the different layers on each disc.  The laser diode is actually the part in the top right in the above photo.  It looks like a small gray box, the gray part is the heat sink and should also be kept.
<p align="center">
  <img src="/images/posts/2009-3-7/diode_block.jpg">
</p>
Here is another view of the laser assembly.  The diode is on the bottom right, and the lenses are in the middle left.  You can see some small glass beam splitters in the center of the photo.  The laser diode’s heat sink block was glued into the assembly with some strong glue.  An X-acto knife and a lot of pressure broke the glue, causing the laser diode to fly across the room.  Eventually, I found it on the carpet.  Hopefully it wasn’t destroyed in the process, especially since it is very sensitive to static electricity.
<p align="center">
  <img src="/images/posts/2009-3-7/diode.jpg">
</p>
The above photo shows both the laser diode, lower left, and the lenses, upper right.  I kept the lenses hoping I could use them to help focus the laser pointer once I had the diode working.

Now I just need a circuit to power it.

Because I plan to add a lot of photos and I want to keep each web page small so they load faster, I have broken this project up into two parts.  Please continue to “Part 2” to see how this project turns out!
