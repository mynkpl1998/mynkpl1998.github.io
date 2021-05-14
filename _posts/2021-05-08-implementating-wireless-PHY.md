---
title: 'Implementing Wireless PHY (WiPHY)'
date: 2021-05-08
permalink: /posts/implement-wiphy
toc: true
tags:
  - Wireless Communication
  - RTL-SDR
  - Amplitude Shift Keying
---

> This blog is about 

I am writing this blog post in May 2021, at the time when people in India are going through the second wave of COVID-19. I hope all of you are fine and taking care of loved ones. If we try to observe the one thing which is keeping us connected during this pandemic is the communication. Without having the good internet infrastrcture we won't be able to get information from place to another and would have made it more difficult to combat this deadly disease. Hence, we can appreciate how important communications have been in our lives.

There are various ways to communicate information from one place to another. But In this blog, we will explore how the digital information is encoded to radio waves which can be then transmitted over the air and received by another radio which attempts to decode/re-construct the information which was sent from received signals.

# Notation Used


# Abbreviation Used

1. TX - Transmmitter
2. RX - Receiver
3. SDR - Software Defined Radio
4. MS/s - Mega samples per second
5. ADC - Analog to Digital converter

# :wave: Introduction

In this blog, we will consider an information source which has digital information (sequence of zeros/ones) which it needs to communicate to other device which is at some distance from it. To transmit this information, at sending end we will need a transmitter (TX) which will encode this digital information over radio waves. The radio waves are then transmitted via antenna and is propogated through the air which reaches the receiver (RX). The job of receiver is then to decoded the information from these wireless signals. The figure shows the flow of information between the two devices.

<center><img src="https://raw.githubusercontent.com/mynkpl1998/mynkpl1998.github.io/master/images/blog_posts_media/implement_wiphy/wireles_comm.png"></center>
<center>This is an image</center>

> NOTE: In this post, the focus is to design a half-duplex wireless link. This implies, the TX and RX is fixed. Only one can transmit and other can receive. Not the other way around. We are particularly interested in building a device which can send unaddressed, unrelibale(without ACK) short messages between the TX and RX. 

# :gear: Hardware Required

As discussed in the previous section, we will need a TX and RX to build such a  wireless link. Apart from that, an Ardunio is also required to hook up the TX module.

### TX
  
  For TX, we will make use 315/433 MHz ASK RF modules (See figure x). These modules are very simple to use and are very cheap as well. The module can be connected to micro-controllers such as Arduino and can be programmed from the same to modulate the digital signal on to the carrier wave which a sine wave of 315 or 433 Mhz frequency. This carrier is then is then transmiited through the on-board antenna.

  > NOTE: There are two varaints of ASK modules, one which make use 315 MHz frequency and the other which uses 433 MHz. Anyone should be fine. I am using 315 MHZ one. If you are using 433 MHZ, then you need to change radio settings in configuration file. More deatils will be followed in the later sections. Further, you can always attach a peace of short wire to the antenna port of the module to improve the signal reception and communication range. 

### RX

  At RX, we will make use Realtek Software Defined Radio (RTL-SDR). This SDR is capable of receveing signals which lies within 24 - 1766 MHz frquency range with sample rate of upto 2 MS/s. The ADC of the SDR has the resolution of 8-bit. We will use the SDR to capture the signals transmitted at 315 MHz and anlalyze those captures to look for the transmitted data.Put a picture

  > NOTE: The SDR connects to the laptop/PC and the samples captured by the SDR can be streamed to the device over USB.

# :electric_plug: Getting the hardware up and running

### Wiring the TX

The TX connects to a micro-controller such as Arduino using three wires. The connections are pretty straight and are summarized in the Fig 3. 

<center><img src="https://lastminuteengineers.com/wp-content/uploads/arduino/433MHz-RF-Wireless-Transmitter-Pinout.png" height="300" width="300"></center>
<center>Fig 3. 433/315 MHz ASK connections pinout. <br>Source: <a href="https://lastminuteengineers.com/433mhz-rf-wireless-arduino-tutorial/">lastminuteengineers.com</a> </center>

Once the connection is made, the Arduino needs to be connected to PC via USB to upload the firmware and send messages via the connected RF module.

## Sanity checks running system performance once the connection is done.

# References

1. <a href="https://lastminuteengineers.com/433mhz-rf-wireless-arduino-tutorial/">https://lastminuteengineers.com/433mhz-rf-wireless-arduino-tutorial/</a>