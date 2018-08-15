# 4. Smart Security Device

In this fourth tutorial, you'll create a "Smart Security" device and program its apps.

## Tutorial Goals

The goals of this fourth tutorial are to help you:

* Gain further experience by creating another practice IoT device and programming its apps
* Become better prepared to create your own IoT device and apps for your team project

## Smart Security System

You'll create a prototype of a "Smart Security" device by modifying your "Smart Light" device \(which has an LED light and push button\) to add a motion sensor and a speaker:

* The **LED light** will be turned on or off to indicate whether the security system is currently "armed" or "disarmed."
* The **push button** will be used to switch the security system between "armed" and "disarmed" mode. \(The button will simulate a security system's keypad, which is used to enter a numeric passcode. For this prototype device, you'll simply press the button to toggle the system between modes, as if you had correctly entered the passcode.\)
* The **motion sensor** will detect whether something is moving within the surrounding area.
* The **speaker** will be used to produce an alarm sound if motion is detected.

You'll program a Photon device app to control the LED, push button, motion sensor, and speaker.

You'll also program a web app that interacts with your Photon over the internet to perform these tasks:

* Monitor the security system's current mode \("armed" or "disarmed"\)
* Remotely toggle the security system between "armed" or "disarmed" mode
* Receive an event notification if the security system detects motion
* View the date and time of the last motion event detected



