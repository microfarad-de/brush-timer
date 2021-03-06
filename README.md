# Very Low Power Kids Toothbrush Timer

<p align="center">
<img src="https://raw.githubusercontent.com/microfarad-de/toothbrush-timer/master/doc/2019-02-25-211951.jpg" alt="drawing" width="400"/>
</p>

This Arduino sketch that implements a funny "little fish" kids toothbrush timer. A detailed documentation of this project can be found under www.microfarad.de/toothbrush-timer.

Unless stated otherwise within the source file headers, please feel free to use and distribute 
this code under the *GNU General Public License v3.0*.

## Theory of Operation

The device features 9 LEDs arranged in a "little fish" pattern. When turned on, 
the eyes of the fish will start to blink once per second. More and more LEDs begin to 
blink as time passes. One of several random animation sequences is activated as soon as the 
recommended two minute tooth brushing duration elapses, then the system will power 
itself off.

The device implements a soft power on circuit using a tactile switch and two 
FET transistors. Briefly pressing the power button will power up the system and initiate
the timer sequence. Pressing the power button during approximately 2 seconds while the  
device is on will skip the timer sequence and directly activate the LED animation 
sequence prior to powering down the system.

The device is designed to consume a very low current and is able to run on a single CR2025 
or similar 3V Lithium cell for thousands of cycles. The current consumption is around 10μA 
during the Power-Down sleep phase and around 1.2mA when all the LEDs are on. The device 
consumes no current when the power is off.

In order to reduce the bill of material, all 9 LEDs share one common dropper resistor.
Turning on multiple LEDs simultaneously is not recommended as it will result in some of 
the LEDs glowing brighter than others. A multiplexing routine is used for sequentially 
turning on one LED at a time and doing this fast enough to create the illusion that they 
are simultaneously lit due the the persistence of the human vision.

This sketch has been implemented and tested on an ATmega328P based Arduino Pro Mini 
compatible board running on 3.3V/8MHz.

It is recommended to activate the watchdog support on the Arduino bootloader
by defining the WATCHDOG_MODS macro. This will reduce the bootloader's power-up 
delay, thus invalidating the need to hold the power button for around 2 seconds for 
the system to turn on.

Arduino’s onbard 3.3V linear regulator as well as the power LED need to be unsoldered as 
they would otherwise significantly increase the overall power consumption.

## Prerequisites

* ATmega328P based Arduino Pro Mini, Arduino Nano or similar model
* Custom bootloader from: https://github.com/microfarad-de/bootloader

## Circuit Diagram

You can find the circuit diagram for this device under the follwoing link:

https://github.com/microfarad-de/toothbrush-timer/raw/master/doc/toothbrush-timer-schematic.pdf




