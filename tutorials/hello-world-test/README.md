# 2. Hello World Test

## Tutorial Goals

The goals of this second tutorial are to help you:

* Verify your Photon device connects to Wi-Fi and the Particle Cloud service
* Understand how to use Particle Build to create Photon device apps
* Create a Hello World app to test your Photon device

## How does Photon connect to Wi-Fi?

When your Photon is powered on \(or restarted\), it will automatically try to connect to a Wi-Fi network.  It does this by using a saved list of Wi-Fi logins \(network names and passwords\). The Photon can be programmed to store login information for up to 5 different Wi-Fi networks.

A brand new Photon will **not** have any Wi-Fi logins saved yet. The Photon provided to you by your teacher should already have one or more Wi-Fi logins programmed into it.

## What is Particle Cloud?

Once your Photon is connected to Wi-Fi, the Photon will automatically try to connect to Particle Cloud, which is a cloud service that Particle provides for all of its microcontroller devices. All of your Photon's internet communications are routed through Particle Cloud.

Particle Cloud can be used to:

* Code and store all your different Photon device apps \(using Particle Build\)
* Update the app stored on your Photon device
* Update the firmware on your Photon device
* Send and receive data between your Photon device app and your web app
* Manage your Photon device remotely

![](../../.gitbook/assets/particle-cloud%20%281%29.png)

## What is Particle Build?

[Particle Build](https://login.particle.io/build) is an online code editor \(web IDE\) provided by Particle.  Particle Build is part of the Particle Cloud platform. You will login to Particle Build to code and store all your Photon device apps.

The Photon device itself can only store and run one app at a time. However, you can create and save multiple apps in Particle Build. When you need to update the specific app stored on your Photon device, you'll do this in Particle Build – and your Photon will download the new app over Wi-Fi.

Your team will need a Particle account to login to Particle Build.  However, your teacher will most likely provide your team with a **pre-existing** Particle account username & password that is already associated with your specific Photon device. Every Photon has a unique device ID that it uses to communicate with Particle Build and Particle Cloud. Each Photon device ID can only be associated with one Particle account.

## What is a Hello World app?

When learning a new programming language, the first step that most people take is to create what is called a ["Hello World"](https://en.wikipedia.org/wiki/%22Hello,_World!%22_program) program. Traditionally, this involves displaying the text "Hello World" on a screen. Often, the program is just a few lines of code. The purpose is to demonstrate that you can create a simple yet functional program in the new coding language.

However, your Photon circuit board does **not** have a built-in screen. Your Photon kit has a micro OLED screen that can be connected to the Photon – but that would require connecting 8 different jumper wires and coding a more complex app.  Eventually, you'll be able to do this, but we need something much simpler for your first experience using and programming your Photon.

The good news is your Photon circuit board has a built-in LED light \(D7\) that can be controlled by your device's app. You won't have to connect any extra parts or wires yet – and you can program a simple app that simply **makes the built-in LED blink on and off repeatedly**, as a way of saying "Hello World."

### Wiring Programming Language

All the apps that run on your Photon device will be coded using Particle's version of the [Wiring](http://www.wiring.org.co/reference/) programming language for microcontrollers.

The [Particle firmware](https://docs.particle.io/reference/firmware/photon/) on your Photon runs a version of the Wiring language that has some minor differences as well as several additions in order to support the Photon hardware.

One example of a minor difference:

* In the original Wiring language, the `analogRead()` method reads the value of an analog input pin and returns the value as an integer \(whole number\) between 0-1023.
* In the Particle firmware, the `analogRead()` method does the same thing but returns the value as an integer between 0-4095.

The Particle firmware contains additional methods that are **not** part of the original Wiring language. For example, there are methods which allow the Photon device to interact with Particle Cloud. There are other methods which can control built-in hardware components on the Photon circuit board \(such as the Wi-Fi module, RGB light, etc.\).

{% hint style="info" %}
**WIRING VS. ARDUINO:**  [Arduino](https://www.arduino.cc/reference/en/) is another programming language commonly used by microcontrollers. It turns out that Arduino was based on Wiring, so the two languages are nearly identical \(though there are some differences\). In most cases, a program originally written in Arduino will work on your Photon with only minor revisions.
{% endhint %}



