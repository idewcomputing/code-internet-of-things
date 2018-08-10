# Particle Cloud

The defining feature of an IoT device is its ability to send and receive information through the internet. This allows an IoT device to interact with other apps or other IoT devices. For this project, you'll be creating a web app that interacts with your Photon device through the internet.

All of your Photon's internet communications are routed through the Particle Cloud service, which offers these three ways that your web app can interact with your Photon device:

1. Web app can **read device variable** through Particle Cloud
2. Web app can **call device function** through Particle Cloud
3. Web app can **get device event notifications** through Particle Cloud

In order to make your Photon interact with your web app, you'll need to add special code to both your Photon device app and your web app:

* The Particle firmware on your Photon device has built-in cloud functions to allow your device to interact with a web app through Particle Cloud. You'll need to add code statements using these cloud functions in your Photon device app.
* There is a Particle API JavaScript library that provides methods \(functions\) to allow your web app to interact with your Photon device through Particle Cloud. You'll need to load this JS library in your web app's HTML file, and then add code statements using the library's methods in your web app's JavaScript file.



