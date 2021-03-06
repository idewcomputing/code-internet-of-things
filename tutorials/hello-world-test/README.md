# B. Hello World Test

In this second tutorial, you'll program a "Hello World" app for your IoT device.

## Tutorial Goals

The goals of this second tutorial are to help you:

* Verify your Photon device connects to Wi-Fi and the Particle Cloud service
* Understand how to use Particle Build to create Photon device apps
* Create a Hello World app to learn how to program your Photon device

## What is a Hello World app?

When learning a new programming language, the first step that many people take is to create what is called a ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program. Traditionally, this program simply displays the text "Hello World" on the screen and only requires a few lines of code. The purpose is to demonstrate that you can create a simple yet functional program in the new coding language. It's the first step before creating more complex programs.

However, your Photon circuit board does **not** have a built-in screen. Your Photon kit does have a micro OLED screen that can be connected to the Photon – but that would require connecting 7 different jumper wires and coding a more complex app.  Eventually, you'll be able to do this – but we need something much simpler for your first Photon app.

The good news is your Photon circuit board has a built-in blue LED light \(D7\) that can be controlled by your device's app. You won't have to connect any extra parts or wires yet – and you can program a simple app that **makes the built-in LED blink on and off repeatedly**, as a way of saying "Hello World."

## Wiring Programming Language

All the apps that run on your Photon device will be coded using Particle's version of the open-source [Wiring](http://www.wiring.org.co/reference/) programming language framework for microcontrollers.

The [Particle firmware](https://docs.particle.io/reference/firmware/photon/) on your Photon runs a modified version of the Wiring language with a few minor differences, as well as some additional methods \(functions\) customized for the Photon hardware.

One example of a minor difference:

* In the original Wiring language, the `analogRead()` method reads the value of an analog input pin and returns the value as an integer \(whole number\) between 0-1023.
* In the Particle firmware, the `analogRead()` method does the same thing but returns the value as an integer between 0-4095 \(providing a higher level of precision\).

The Particle firmware contains additional methods \(functions\) that are **not** part of the original Wiring language. For example, there are methods which are used to make the Photon interact with Particle Cloud. There are methods which can be used to control built-in hardware components on the Photon circuit board \(such as the Wi-Fi module, RGB light, etc.\).

{% hint style="info" %}
**WIRING VS. ARDUINO:**  [Arduino](https://www.arduino.cc/reference/en/) is another programming language framework for microcontrollers. It turns out that Arduino is based on Wiring, so the two languages are nearly identical \(though there are some differences\). In most cases, a program originally written in Arduino will work on your Photon with only minor revisions. So once you've learned how to program in one of these languages, you've basically learned both.
{% endhint %}

{% hint style="info" %}
**WIRING VS. C++:**  Wiring \(like Arduino\) is a programming framework written in C++, so you can also directly incorporate C++ code within your device app.
{% endhint %}

