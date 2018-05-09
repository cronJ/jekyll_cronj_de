---
layout: post
title: "Getting NodeMCU running on a ESP-01 module in 2016"
date: 2016-01-24 13:41:00 +0200
categories: electronic
---
<h2>Introduction</h2>
I tried to install NodeMCU with the help of my article from january 2015, but had some problems to do so. So I write a new article with a new approach, which works today. I also try to provide all new informations in englisch, because my site statistics say most of my visitors came from EU.
<h2>Connection</h2>
For the connection we need a serial interface. I use an FTDI UM232R module for this. To define the numbers on the ESP-01 module I use this drawing I created:

<a href="https://cronj.de/2015/01/31/nodemcu-auf-esp8266-esp-01-modul/esp-01_pinnumber/" rel="attachment wp-att-404"><img class="alignnone size-full wp-image-404" src="https://cronj.de/wp-content/uploads/2015/01/ESP-01_PinNumber.png" alt="ESP-01_PinNumber" width="260" height="160" /></a>
<ol>
	<li>GND</li>
	<li>UTXD</li>
	<li>GPIO2</li>
	<li>CH_PD</li>
	<li>GPIO0</li>
	<li>RST/GPIO16</li>
	<li>URXD</li>
	<li>VCC</li>
</ol>
You need at least three signals from your serial interface to the ESP-01 module. The signals are ground, RxD and TxD. The 3.3V supply voltage comes from my programmable power supply. The updated connection list is shown above.
<pre class="lang:default highlight:0 decode:true">VCC   -&gt; 3V3
GND   -&gt; GND
RST   -&gt; 3V3
CH_PD -&gt; 3V3
URXD  -&gt; DB0 (UM232R)
UTXD  -&gt; DB1 (UM232R)
GPIO0 -&gt; GND
GPIO2 -&gt; floating</pre>
The jumper JP1 on my UM232R module is set between pin 1 and 2 which defines 3.3V for the IOs.
<h2>Preparations for flashing NodeMCU</h2>
First we need the NodeMCU firmware. In the previous article you could download a pre-build binary from the GIT repository. I didn't found a pre-build firmware on the repository today, so we have to build our own. Luckily there is an easy online firmware builder: <a href="http://nodemcu-build.com/index.php">nodemcu-build.com</a>.

You have to enter a real email address, because you get your firmware download links via mail. I choose the master branch for my build and leave the default modules checked for a quick test. Then you have to click the "Start your build" button on the bottom of the page and wait until you got mail. I got two versions in the mail. One is labeled as an integer version and one as a float. For this article I'm using the integer one.
<h2>Flashing</h2>
To flash the actual firmware I used a tool called <a href="https://github.com/nodemcu/nodemcu-flasher">nodemcu-flasher</a>. I downloaded the 64bit version.

At this point be sure:
<ul>
	<li>you connected your ESP-01 module to your serial interface</li>
	<li>your module is supplied with a voltage of 3.3V</li>
	<li>GPIO0 is set to ground and was at ground on power-up</li>
	<li>CH_PD is set to VCC to enable the module</li>
	<li>your serial interface is recognized by your OS</li>
</ul>
Now you can start the nodemcu-flasher. By default it will flash an integrated NodeMCU firmware, which can be outdated. Go to the "Config"-tab to select the new firmware you just created in the step before.

[caption id="attachment_408" align="alignnone" width="300"]<a href="https://cronj.de/2016/01/24/getting-nodemcu-running-on-an-esp-01-module-in-2016/config_tab_default/" rel="attachment wp-att-408"><img class="wp-image-408 size-medium" src="https://cronj.de/wp-content/uploads/2016/01/config_tab_default-300x175.png" alt="config_tab_default" width="300" height="175" /></a> Default settings[/caption]

[caption id="attachment_409" align="alignnone" width="300"]<a href="https://cronj.de/2016/01/24/getting-nodemcu-running-on-an-esp-01-module-in-2016/config_tab_own_build/" rel="attachment wp-att-409"><img class="wp-image-409 size-medium" src="https://cronj.de/wp-content/uploads/2016/01/config_tab_own_build-300x175.png" alt="config_tab_own_build" width="300" height="175" /></a> My own firmware[/caption]

Go to the "Operation"-tab and press the "Flash (F)" button to start the flash operation. The AP MAC and STA MAC should display correct values. If not and the progress bar don't move, turn your module off and on again to enable flash mode. In flash mode wait until the progress bar is completely filled.

[caption id="attachment_410" align="alignnone" width="300"]<a href="https://cronj.de/2016/01/24/getting-nodemcu-running-on-an-esp-01-module-in-2016/operation_tab_flashing/" rel="attachment wp-att-410"><img class="wp-image-410 size-medium" src="https://cronj.de/wp-content/uploads/2016/01/operation_tab_flashing-300x175.png" alt="operation_tab_flashing" width="300" height="175" /></a> Firmware is being flashed[/caption]

[caption id="attachment_411" align="alignnone" width="300"]<a href="https://cronj.de/2016/01/24/getting-nodemcu-running-on-an-esp-01-module-in-2016/operation_tab_flashing_done/" rel="attachment wp-att-411"><img class="wp-image-411 size-medium" src="https://cronj.de/wp-content/uploads/2016/01/operation_tab_flashing_done-300x175.png" alt="operation_tab_flashing_done" width="300" height="175" /></a> Flashing completed[/caption]
<h2>Check your firmware</h2>
After flashing we need to check if the firmware is working. Turn off your ESP-01 module and remove GPIO0 from ground then power it on again. Connect with an terminal software to the serial interface which connects to your module. The baud rate has to be 9600.

For testing purpose I connected an red LED and a 470Ohm resistor in series to ground on GPIO2. In your terminal software you set GPIO2 to an output. The GPIO2 has the IO pin defined to 4! Your terminal should show something like this:
<pre class="">NodeMCU custom build by frightanic.com
branch: master
commit: c8037568571edb5c568c2f8231e4f8ce0683b883
SSL: false
modules: node,file,gpio,wifi,net,tmr,uart
build built on: 2016-01-24 10:52
powered by Lua 5.1.4 on SDK 1.4.0
lua: cannot open init.lua
></pre>
Now I enter the following line to set the IO pin to an output:
<pre>gpio.mode(4, gpio.OUTPUT)</pre>
To switch the LED on I enter:
<pre>gpio.write(4, 1)</pre>
or:
<pre>gpio.write(4, 0)</pre>
to turn the LED off.

If you can control the LED with this commands, congratulations, your NodeMCU firmware works.