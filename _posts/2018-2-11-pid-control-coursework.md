---
layout: post
title:  "PID Control Coursework"
date:   2018-2-11 11:16:01
categories: control systems
excerpt_separator: <!--more-->
---

![First step test](/images/001pidcoursework/00overview.jpg?raw=true "First Step Test")

Feedback Control was one of those subjects that couldn't be experienced in its fullest without experimenting a “real life” application.

We were given a group task to design a PID control loop to a temperature system. We were provided a few components such as a 12 volts 21 W bulb lamp, a computer fan, and a LM35 temperature sensor. Everything else such as the mock-up, power driver, sampling circuit, digital control system was our own decision and design.<!--more--> My coworkers were Henrique Eduardo Felipini, Mateus Sant'Ana, Murilo Ramos Carraro and Vilmarque João Junior.

The controlled variable was temperature, the manipulated variable was the lamp power which was required to be driven proportionally and the disturbance was the fan ventilation, which should be on but in order to simulate a disturbance it should be switched off.

We wanted to experiment different dead time so we designed the system in a way we could change the position of the temperature sensor. Here is the very first sketch.

![First sketch](/images/001pidcoursework/01sketch.jpg?raw=true "First Sketch")

And here some from the fabrication process. I really enjoyed making it!

![Fabrication](/images/001pidcoursework/02fabrication.png "Fabrication")

It turned out like this.

![The system](/images/001pidcoursework/03system.jpg "System")

We had this idea of using Arduino as controlling device, so the sensor data collected was sent over serial to Matlab where we had it plotted real time. This data was then used to approximate two models. A first order (single pole) linear system with dead time and a second order linear model.
<video width="640" height="480" controls="controls">
  <source src="/images/001pidcoursework/04stepresponse.mp4" type="video/mp4">
</video>

Later on we moved from the Arduino to a DAQ system as we were having difficulties with the Arduino’s analog output (PWM).

The signal conditioning circuit we have designed allowed us to adjust via trimpots the gain and the offset, so the signal could fit the best in the 0-5V ADC range with a high input impedance. The output circuit was designed so the 0-5V (40mA) microcontroller could be transformed into a 12V 1.7A output that driven the power to the lamp proportionally.

Several PID tuning methods were used such as Chien-Hrones-Reswick, AMIGO, IMC, Matlab root locus PI and PID design, with or without anti-windup. The design methods were analysed regarding rise time, control saturation, overshoot and disturbance rejection.

We concluded that the best performance was achieved by the PI controller designed using root locus. PID had too much bad influence from signal noise.








