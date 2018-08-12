# Call Device Function

Your Photon device app can share a custom function through Particle Cloud, so your web app can call the function to make it run on your Photon device.

For example, your Photon device app could share a custom function that toggles an LED light on or off, so your web app would be able to call this function to turn the light on or off.

![](../../.gitbook/assets/particle-cloud-function.png)

Your Photon device app will use the `Particle.function()` method to share the value of a device variable through Particle Cloud.

A "cloud function" will be created that will call the function on your device.

Your web app will use the `particle.callFunction()` method to read the value of your cloud variable.

## Photon Device App

Particle.function\(\)

## Web App JS

particle.callFunction\(\)



