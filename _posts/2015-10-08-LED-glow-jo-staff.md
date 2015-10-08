---
layout: post
title:  "LED glow jo staff"
date:   2015-10-06 11:33:00
categories: electronics LED arduino jo staff
---

I've been working on and thinking about this project for a few months.  I have all the parts and a workable design so it is time to assemble the **LED Glow Jo**


###Design requirements:###

* Same length, weight, diameter as a regular aikido jo staff (approx 1" diameter and 5" long weighing 2 lbs.)
* Sturdy enough to survive moderate use with some strikes
* Packed with enough RGB LEDs to be super bright and lit up on all sides
* Microprocessor to drive the lighting patterns
* Accelerometer and maybe other sensors to modulate the patterns
* Enough power to drive the LEDs for a few minutes on max power
* Actually be able to fit everything in and remove it for servicing, charging, etc
* Must not melt, explode, or catch fire

###Polycarbonate tube###

My design uses a 1" outer diameter polycarbonate tube. This had a 7/8" inner diameter and is super strong but somewhat more flexible than I'd like. I think it will stiffen up once the contents are packed in.

###Addressable LED Strip Lighting###
The [WS2812 RGB led strips](https://www.sparkfun.com/products/12025) are small enough that I think I can fit 3 of them along the length of the tube with enough room for AA batteries in center.  The LED strips that I'm using have 60 tri-color LEDs per meter and since I need 5 meters of the LED strips this equates to **300** LEDs (actually 900 diodes since each RGB LED is built from 3 diodes). This ends up requing several **Amps** of current when they are turned up to full power!

###Power Supply###

In order to power all of this brightness I need to pack the core of the tube with AA batteries: a lot of them. I was originally thinking of using 20 AA batteries arranged with 4 series, 5 parallel to give 6v and 5 (?) amps. But then I decided to use rechargeable batteries and realized that the [5V LM7805CV voltage regulators](https://www.sparkfun.com/products/107) i'm using want 7V minimum and I had to re-adjust the battery array. I decided to just go with NiMH rechargeable AA batteries arranged in 6 series, 3 parallel (18 total) for 8.4V and a couple of amps. I'm adding some capacitors to provide boost current and these things are plenty bright without having to go overboard on the current. I'm using a one regulator for each stip and one for the arduino so there will be 4 regulators. Each of them should be able to drive 1.5 amps but I assume that will make them overheat since I don't have much of a heat sink plan to dissipate heat.


###Supercapacitors###

I just had to throw a few of these [10F supercapacitors](https://www.sparkfun.com/products/746) in. They are only 2.5V rated so I am arranging them in series to give 5F 5V cap modules that will supplement the battery current output. I'm still experimenting with these guys and trying not to melt anything in the process!

###Removable Core###

One thing that I realized right away is that I need to be able to slide everything in and out of the outer tube. I got some polycarbonate sheet and cut it into .7" by 5' strips which are connected lengthwise and then folded into an equilateral triangle core to support the batteries and components. This will (hopefully) allow me to slide it in and out and prevent anything from getting stuck in the tube. Turns out it is challenging to fit the AA batteries in the center so I have had to cut out parts of the strips to allow it to slide in and out without too much friction and still support the components. The LED strips go on the outside of the triangular core and the batteries, supercaps, voltage regulators, arduino, etc goes in the middle.

###Arduino Microprocessor###

This very small [Arduino Pro Mini 328 - 5V/16MHz](https://www.sparkfun.com/products/11113) arduino fits in the tube and I went with the 5V model so I can directly drive the LED strips which expect a 5V control signal. I'm using the [Adafruit NeoPixel library](https://github.com/adafruit/Adafruit_NeoPixel) to control the LEDs which is working pretty well so far. The software part of this hasn't really gotten far but I can make the strips light up and change the brightness and patterns.

I've been trying to figure out the best way to construct everything so had to think about it for a while. It is a mess right now but starting to come together as you can see:

<img src="/images/20151008_095038.jpg">

Additional features I'd like to try to add at some point:
* some super bright white LEDs on the ends for flashlight abilities aka Gandalf staff efects
* other interesting sensors
* other interesting outputs: speakers, etc

