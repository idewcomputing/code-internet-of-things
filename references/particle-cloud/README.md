# Particle Cloud

The defining feature of an IoT device is its ability to send and receive information through the internet. This allows an IoT device to interact with other apps or other IoT devices. For this project, you'll be creating a web app that interacts with your Photon device through the internet.

All of your Photon's internet communications are routed through the Particle Cloud service, which offers these ways that a web app can interact with a Photon device through Particle Cloud:

1. A web app can **get the value of a Photon device variable**
2. A web app can **call a custom function on a Photon device**
3. A web app can **get event notifications from a Photon device**

![](../../.gitbook/assets/particle-cloud%20%281%29.png)

In order to make your Photon device interact with your web app, you'll need to add special code to both your Photon device app and your web app:

* The Particle firmware on your Photon device has built-in cloud functions to allow your device to interact with a web app through Particle Cloud. You'll need to add code statements using these cloud functions in your Photon device app.
* There is a Particle API JavaScript library that provides methods \(functions\) to allow your web app to interact with your Photon device app through Particle Cloud. You'll need to load this JS library in your web app's HTML file, and then add code statements using the library's methods in your web app's JavaScript file.



