---
title: Simple Clock
layout: project
thumbnail: simple-clock.jpg
type: personal
excerpt: Simple Clock
priority: 110
---

<h3>Simple Clock</h3>

<p>Simple 7-segment bedside clock with varying light intensity levels. This clock allows me to quickly find out what the current time is due to its bright screen and how big the digits are. At nighttime, the brightness of the digits decreases significantly in order to be visible at night while not disturbing whoever might be sleeping.</p>

<p>After using the project for a few months, I can say with confidence that it completes its intended goal of keeping me aware of time while not disturbing me when I sleep without having to interact with it in any way.</p>

![Prototyping on a breadboard]({{ site.url }}/assets/images/content/sized/simple-clock/breadboard.jpg)

<h3>Features</h3>

<ul>
  <li>Syncs with online clock - Always up to date when the time changes. The clock still works without an internet connection</li>
  <li>Automatic screen dimming - Allows me to not have to worry about manually dimming the screen at night</li>
</ul>

<h3>Future Expansions</h3>

<ul>
  <li>Alarm - In order to not have to depend on my phone in order to wake me up</li>
  <li>Humidity/Temperature sensor - To figure out if I’m overheating due to stress or because the room temperature is rising</li>
  <li>Intruder alarm - To make sure that there are no intruders when I’m not in the room</li>
  <li>Light sensor - To better determine to dim the numbers</li>
  <li>Battery - For when the power runs out in the middle of the night</li>
</ul>

<h3>Supplies</h3>

<ul>
  <li>1 x Photon microcontroller</li>
  <li>1 x Enclosure</li>
  <li>3 x Prototyping board</li>
  <li>1 x _____uF capacitor</li>
  <li>1 x _____ resistor</li>
  <li>1 x MAX7219 driver</li>
  <li>Glue</li>
  <li>Bunch of wires</li>
  <li>Male and Female wire connectors</li>
  <li>Soldering equipment</li>
</ul>

<h3>Materials</h3>

<p>Like my previous IoT project (Timer Reminder), I used a cheap enclosure that I bought at Michael’s. The size of the chosen enclosure also allows me to easily add more components to the clock in order to make it even more useful. Finding 7-Segment digits of the chosen size (1in.) turned out to be difficult, but ultimately found a seller on eBay who had what I needed. The microcontroller I chose is the Photon. I chose the Photon primarily because it allowed me to get the time without having to worry about provide a method of setting the time or having to keep the project powered at all times.</p>

![Enclosure with the holes for the screen cutout]({{ site.url }}/assets/images/content/sized/simple-clock/box-with-holes.jpg)

<h3>Build Process</h3>

<p>The internals of this project is divided into two separate boards, one for the digits and one for the microcontroller. The two boards share the same problems, constraints, and downfalls. Due to the fact that 7-segment screens have some many leads that need to be chained, wiring up the screen and all the other components turned out to be a good mental puzzle. Ultimately I came up with a wiring scheme that I wasn’t completely satisfied but decided to continue with in order to keep the project alive and progressing. My dissatisfaction with the design was mainly due to the physical complications of having to solder of the two sides of the PCB without having much clearance. If I had to do it again, I would learn how to make my own PCB boards with a milling machine or through another process.</p>

![Digits Front]({{ site.url }}/assets/images/content/sized/simple-clock/digits-front.jpg)
_Digits Front_

![Digits Back]({{ site.url }}/assets/images/content/sized/simple-clock/digits-back.jpg)
_Digits Back_

![Final]({{ site.url }}/assets/images/content/sized/simple-clock/final.jpg)
_Final_