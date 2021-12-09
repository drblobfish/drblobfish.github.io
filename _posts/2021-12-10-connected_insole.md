---
layout: post
title: "Générateur de voeux d'anniversaire"
description: "Creating an opensource connected insole with pressure sensor for podological diagnosis"
---

[tl;dr] As a personnal project, I worked on an insole with pressure sensor that communicates via Bluetooth to a web app that you can test at this address : https://drblobfish.github.io/connected_insole/

# Background

The Connected Insole project began under the name of YAWO during the 2019 SDG Summer School at CRI.

Their goal was to produce a "connected insole ( a wearable insole) for diabetic patients suffering from Type 2 diabetes. The insole would consist of several pressure sensors to give dynamic feedback of the patients’ plantar pressure. This data would be continuously processed and the user/doctor would be provided with an alert when a disorder was detected. Based on the received input the user could correct his/her walking stance".

More information on the project can be found on those links :

https://paper.dropbox.com/doc/SDG-Team-2-YAWO-dHzXFzb93E2nyiA1Ohzqh

https://projects.directory/projects/zCfr1Jez/summary

<p align="center">
    <img src="/assets/images/insole/YAWO.png" width="95%">
    <br />
    <i align="center">Final prototype of the summer school – picture from the YAWO team</i>
</p>


They achieved to build an insole with DIY pressure sensors able transmit data through Arduino serial protocol to a processing script.

This work was a great proof of concept but several points needs to be improved for the device to be a usable product such as wireless communication.

# Goal

My goal for this project is to work on wireless communication between the insole and an app installed either on a phone or on a computer.

However, I worked with slightly different material than the YAWO team as I was provided with a commercial insole-shaped pressure sensor matrix.

# Hardware

## The Insole

The insole used, the RX-ES42-16P, is a 3×6 pressure sensor matrix between two plastic sheet. It consists of 16 pressure sensors organized as follows.

> A matrix is an efficient way of packing a lot of sensors while using less pins : we define column and row pins connected to multiple sensor such that each pair row pin/column pin is only connected to one sensor. Then if we take measures between one row and one column at a time, we can measure all n sensor while only using √ n digital output pins and √ n analog input pins.

<p align="center">
    <img src="/assets/images/insole/schem_insole.png" width="95%">
    <br />
    <i align="center">Schematics of the RX-ES42-16P insole</i>
</p>


## The Micro-controller

As a micro-controller, I used a Feather nrf 52.

<p align="center">
    <img src="/assets/images/insole/nrf52.jpeg" width="95%">
    <br />
    <i align="center">Picture of a nrf 52 Feather board - picture from adafruit's website</i>
</p>


This Arduino-compatible board is able to communicate through the Bluetooth Low Energy (BLE) protocol.

## The circuit

Usually when dealing with electrical matrix, multiplexers are used to reduce the number of pins used.

> A multiplexer is an electrical component that essentially behave like a switch that can connect one input pin to a single output pins and that is controlled electronically. The advantage is that if you have n output pins, you only need log2(n) bits to encode the information about which pin you want to connect. For example, if I need to measure 8 sensors, I could use 8 analog input pins but I could also connect all the sensors to a single analog input pin through a multiplexer and control the multiplexer with only 4 digital output pins.

<p align="center">
    <img src="/assets/images/insole/mux_fond.png" width="95%">
    <br />
    <i align="center">Schematics of a multiplexer</i>
</p>


The feather micro-controller has 6 analog input pins, and I didn’t need to connect the board to other things, so after experimenting with multiplexers I choose to not use them for simplicity.

The circuit is thus really simple.

<p align="center">
    <img src="/assets/images/insole/schematics_matrix.png" width="95%">
    <br />
    <i align="center">Schematics of the circuit used</i>
</p>


# Arduino code

Link to the code : https://github.com/drblobfish/connected_insole/tree/main/arduino/ble_sensor/ble_sensor

## Reading the sensors

I created a table that links each of the 16 sensors to its column-row pair. To read all the sensor, the feather nrf 52 board only has to iterate over this table, send power to the column pin and not to the other columns, then read the correct row pin.

## Bluetooth support

I stole the code for Bluetooth from a tutorial made by Sayanee Basu for the website hutscape.github.io and distributed under the MIT licence.

https://github.com/hutscape/hutscape.github.io/blob/master/_tutorials/web-ble-gatt/web-ble-gatt.ino

I didn’t even changed the advertising name of the device :/

Even though the example code only sends integers, it turned out that it can send arrays of integers without any modifications.

# Web App

Link to the code : https://github.com/drblobfish/connected_insole/tree/main/web_app

Test the app by yourself : https://drblobfish.github.io/connected_insole/ (I added an option to generate random number so that you can test the data viz I created even if you don't have access to the insole)

## A quick story about me wasting time

Once we have a device sending data via Bluetooth, we need an app to receive it.

Since the beginning there was two possibilities : either making a phone app or a web-based app. Indeed, while Bluetooth was until now a technology mostly used with mobile devices, it is now possible to connect Bluetooth device directly from a browser thanks to the Web Bluetooth API (it is however not available in Firefox).

<p align="center">
    <img src="/assets/images/insole/web_ble.png" width="95%">
    <br />
    <i align="center">Web Bluetooth API on chrome browser</i>
</p>


My choice was initially to build a native phone app. The final goal of this project would be for the insole to store the data locally, for example on a small flash memory card, and then to upload all the data at once to a computer, however, I feared that I wouldn’t achieve this goal in 3 month ( and indeed I didn’t). I felt that creating a system that would just stream the data to the computer in real time would be more manageable. Yet, if you want to record what the insole is sensing for a 15 min walk, you’ll have to stay around the device that is recording (and BLE has a scope of around 10m), which is easier if this device is a mobile phone and not a big computer.

However, after 2 months, plenty hours of react native courses watched, way to much incomprehensible bugs and still no results, Kevin from the makerLab shared with me the example code from Sayanee Basu that used the Web Bluetooth API, which worked so easily when I tried to test it on my side that I decided to just throw away 2 month of work, essentially switching to a web-based approach.

Solving exploration–exploitation dilemma has never been my strength : I should have considered longer the two possibilities before investing that much time into learning native app development.

## Ble Manager

To manage Bluetooth communication, I used once again used the code from the tutorial made by Sayanee Basu for the website hutscape.github.io.

https://github.com/hutscape/hutscape.github.io/blob/master/_tutorials/web-ble-gatt/web-ble-gatt.html

I refactored it to be more object-oriented, by packing it into an class. The goal was to make a piece of code easily reusable,which, I think, was a success. Indeed after my refactor, you only need to import my small module, create a new bleManager instance, give it some parameters, like the name of the device or the events to execute each time a new value is sent through Bluetooth. Then the user only access the Bluetooth manager through 3 functions : one for connecting a device, one for starting data streaming and one for stopping data streaming (this was already in the example code I stole from).

## Interface

I created the web App with React as framework (mostly because I wanted to use what I had learned while learning react native).

To display the data from the insole I created a basic svg component with the ability to control the opacity of the sensor fill color. Even if its quite pretty I have concerns about the readability of this interface... Guess I’m not a real UX designer.

<p align="center">
    <img src="/assets/images/insole/web_app.png" width="95%">
    <br />
    <i align="center">Screenshot of the final web app</i>
</p>

## Improvements

Loads of improvements are possible for this project :

- Using multiplexer to optimize the number of pin used and eventually use a smaller micro-controller.

- Work on power management for the insole : until now the system is powered by an usb cable !

- Allow the web app to record the data and send it to a database or save it in a csv file.

- Create an other mode where the insole stores the data in a flash drive then upload everything in bulk.

- Create a better visualization of the sensor data : maybe just changing the color ramp could make the data easier to read

- If you want to work on this project, don't hesitate to contact me and to visit the makerLab at CRI to test the prototype we made.

# Links

All my code is available on GitHub :

https://github.com/drblobfish/connected_insole


You can still test the web app: 

https://drblobfish.github.io/connected_insole/