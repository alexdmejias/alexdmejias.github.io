---
title: Timer Reminder
layout: project
thumbnail: timer-reminder.jpg
github: timer-reminder
type: personal
excerpt: Physical Time Tracking Button
priority: 100
---

![timer reminder image]({{site.url}}/assets/images/content/sized/timer-reminder/on-large.jpg)

<h3>Problem</h3>

<p>As someone who works for a design agency, I am required to track the hours for each project that I work on. Tracking hours in itself is not difficult due to how many services there are that do this quite well however, the issue that I have is forgetting to actually start and stop tracking my hours. The problem I was having with the applications that remind me to track my hours every so often is that it is fairly easy to ignore the alarms when you are focused on a task.</p>

<h3>Solution</h3>

<p>I have thought of different solutions for this problem. I thought about using software to automate the data recording processing, but just like other timers that I had used in the past, I would probably forget about them. I thought about using a device like the Digispark (which is essentially an ATTiny85 in a USB pluggable form factor with some LEDs mounted on top of it) could have been a good solution. None of the solutions that I had really felt like something that would be omnipresent and be able to constantly remind me, they both depended on the status of my computer. After sometime, I realized that a button that could just be pressed and record times in which it was pressed would be ideal for me. I would then have to get the data out somehow and make some sense of it, but the button concept did seem appealing. Then the question popped into my head, what if the button could be expanded into something more autonomous?</p>

<p>The final solution that I came up with is a giant physical button that sits on your desk (next to your monitor preferably). The giant button acts as both an indicator and a reminder to actually track your time. Since the concept is fairly simple, expanding on this idea without interfering with the main objective shouldn’t be a problem.</p>

<p>The button has two states, active and inactive. If the button goes from an inactive to active state, it will internally store the time in at which it was pressed and the lights will be powered on.. When the button goes from an active to inactive state, the lights turn off and the button logs the time in which the state changed, it then records the previous start time and the end time in a Google Spreadsheet (through the use of Temboo). The user would then be able to log in to easily annotate the client and/or project for which they worked in the stored time spans. When the button is in the inactive state and the current time is still within the user's previously defined working hours, the button will periodically remind the user to activate the button (by pressing it) in order to track the user's time. The button reminds the user by flashing random light patterns and by playing different sounds.</p>

<h3>Supplies</h3>

<p>The final iteration of the project uses</p>

<ul>
  <li>1 x Arduino Yun</li>
  <li>1 x 24 LED ring, compatible with the NeoPixel Library</li>
  <li>1 x Enclosure</li>
  <li>1 x Giant arcade button</li>
  <li>1 x Prototyping board</li>
  <li>1 x 1000uF capacitor</li>
  <li>1 x 104 capacitor</li>
  <li>1 x 10k resistor</li>
  <li>1 x 1k resistor</li>
  <li>Glue</li>
  <li>Bunch of wires</li>
  <li>Male and Female wire connectors</li>
  <li>Soldering equipment</li>
</ul>

<h3>Process</h3>

<h4>Microcontroller</h4>
<p>At first, I thought about using my Particle Photon for it is small form factor and because I had not been able to use since I bought and wanted to see what it could do. While doing some research for the project, I stumbled upon Temboo, a great service that allows people (and companies) to more easily interface with 3rd party APIs. Aside from the fact that Temboo has the exact integrations with Google Spreadsheets that I needed, it also gives the user the ability to quickly copy and paste the necessary code for the Arduino to make the necessary API request. To speed up this project up, I ended up switching the Photon for the Yun. In this project I wanted to really focus on the physical side of things and because of this, the ability to not focus on the code significantly sped up the project timeline. I could have written a middleman application that handled the Oauth handshake and the Google Drive API handling, but the ability to have the data insertion part of the application be done in about 20 minutes made this project really enjoyable and not worth redoing, as the Temboo option did exactly what needed to be done</p>

<h4>Electronics</h4>

![timer reminder image]({{site.url}}/assets/images/content/sized/timer-reminder/proto-board-large.jpg)

<p>Outside the microcontroller there are only two main components, the LED ring and the button. All the necessary connectors, capacitors, and resistors are connected to a prototyping board mounted on the Arduino, making it a pseudo shield. The hardest part of this was bending the leads of the connectors to match the non-standard pitch of connector that the Arduino uses. Instead of soldering the cables for the button and the LED ring directly to the board, I decided to use regular connectors. The use of connectors should make the project easier to maintain and upgrade later on.</p>

<p>A few things to note about the electronics in the project are that Adafruit recommends connecting a 1000uF capacitor across power and ground between the power source and the cables going out to the LED ring. A 1k resistor is also placed in front of the data line going to the LED ring according Adafruit's advise.</p>

<p>For the button, one thing to note is that since the button uses hardware interrupts, a 104 capacitor is placed between the leads of the button. A 10k resistor should also be placed after the data cable, connecting data and ground.</p>

<h5>Button</h5>

![timer reminder image]({{site.url}}/assets/images/content/sized/timer-reminder/button-open-large.jpg)

<p>Because the button that I had seemed to have issues with the signals that it was sending, I removed all of the buttons electronic components. In order to make the button work without any of its electronic components, I placed a small tactile button under the big button, so it could be pressed every time the bigger button is pressed.</p>

![timer reminder image]({{site.url}}/assets/images/content/sized/timer-reminder/tactile-button-large.jpg)

<h5>Lights</h5>

<p>The second major component of the project are the lights. Originally I thought about using the same LED that came with the button. However, after some initial testing, I noticed that the button had low visibility during the day so I removed the included LED. Next, I thought about connecting four LEDs and putting them through four holes that were already in the enclosure (not sure why there were four predrilled holes). The LEDs would have been controlled through a shift register in order to save the valuable PWM pins on the Arduino. After some more testing and hole drilling, I decided that even with four LEDs the button would not be bright enough for daylight visibility. To mitigate the brightness issue, I thought about installing an additional four LEDs. Only after drilling another set of four holes did I realize that I would now have to manage 16 cables ((ground + vcc) * 8). Only after stepping back for a while, did I realize that I could use a recently purchased LED ring.</p>

![timer reminder image]({{site.url}}/assets/images/content/sized/timer-reminder/holes-large.jpg)

<p>The chosen ring is compact enough to be placed between the light diffuser and the part of the button that will press the tactile button. It has 24 individually controlled SMD RGB LEDs driven by WS2812 chips. Furthermore, the ring is chainable and compatible with the NeoPixel library and only requires a total of three cables. It is recommended to also place a capacitor between ground and vcc and a resistor to the data line.</p>

<h5>Power</h5>

<p>Because the Arduino Yun does not have an internal power regulator, it is recommended that you power the Arduino through the micro USB cable. Although a power regulator could have been added to enable other power sources and make the project more versatile, I decided to follow the recommendation, and power the Arduino through a micro USB cable extruding from the back of the enclosure. Using the Micro USB should still allow me to power the device through USB adapters and external cell phone batteries.</p>

<h4>Enclosure</h4>

<p>For the project, I had to make three modifications to the enclosure. First, I had to drill a hole in the center for the top cover in order to mount the button. Second, I had to glue the platform where the tactile button would be sitting, which was made from scraps of wood I had laying around. The last modification was the hole in the back side of the box for the USB cable to go through. As you might have been able to tell, I decided towards the end of the project to use a bigger enclosure. The reason for the bigger box is that after adding the capacitor and the platform for the tactile button, the box would no longer close.</p>

<p>Due to a miscalculation when I first started, halfway through the project I had to change the enclosure to a bigger box. The miscalculation resulted in not having enough room for the capacity to sit comfortably with the lights.</p>

<p>The larger box allows for easier maintenance and for other additions in the future to be added in the future.</p>

<h4>Code</h4>

<p>The code is fairly simple. When the button is pressed, an interrupt signal is sent that changes the state of the application. If the application is active, the lights will be turned on. If the state is inactive, the lights will light up periodically in different patterns in order to remind the user to activate the button. When the button is first activated the start time is recorded, once the button is pressed again, the end time will be recorded and a request will be sent to Temboo to log the time into the spreadsheet.</p>

(link: https://youtu.be/rp0n5qz-dMU text: Breathing Pattern)
(link: https://youtu.be/ZX8ICTGhWok text: Rotating Lights Pattern)

<h3>Possible upgrades</h3>

<p>There are quite a few things that can be improved or added here, here is a short list.</p>

<ul>
  <li>Screen indicating how much time has passed.</li>
  <li>Authentication: Once the timer is started or stopped a confirmation message can be sent to the user's phone asking for approval</li>
  <li>Notifications for when the timer is started or stopped</li>
  <li>Notifications alerting the user of unlabeled time slots</li>
  <li>Blink the active lights in accordance of the Pomodoro technique</li>
  <li>On/Off Switch</li>
  <li>Improve the button pressing mechanism</li>
  <li>Add another smaller light ring inside the larger one</li>
</ul>