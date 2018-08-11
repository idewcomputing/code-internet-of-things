# Read Device Variable

Your Photon device app can share a variable through Particle Cloud, so your web app can read the value of the variable.

For example, your Photon device could measure the temperature of a room using a sensor, store the measurement in a variable, and share this variable through Particle Cloud, so your web app can read the variable's value and display it.

![](../../.gitbook/assets/particle-cloud-variable.png)

Your Photon device app will use the `Particle.variable()` function to share the value of a device variable through Particle Cloud.

A "cloud variable" will be created to store the value of your device variable. Whenever the value of your device variable changes, the value of the cloud variable will be automatically updated to match.

Your web app will use the `particle.getVariable()` function to read the value of your cloud variable.

## Photon Device App

To share the value of a Photon device variable through Particle Cloud, add this code statement \(be sure to modify\) **within** the `setup()` function of your Photon app:

```cpp
Particle.variable("myVariable", myVariable);
```

The Particle.variable\(\) function requires two parameters inside its parentheses \(in this order\):

1. **The cloud variable name**, which can be up to 12 characters in length. To keep things simpler, make your cloud variable name match your device variable name. However, the cloud variable is allowed to have a different name. The cloud variable name must be listed within double quotation marks. Change `"myVariable"` to the actual name that you want to use for the cloud variable.
2. **The Photon device variable name**, which is the variable in your Photon device app whose value will be shared in Particle Cloud. Change `myVariable` to the actual name of the variable in your Photon device app that you want to share.

**NOTE:** The only data types that are allowed to be shared as cloud variables are:

* `int` \(whole numbers\)
* `double` \(decimal numbers\)
* `String` \(text, up to 622 characters\)

Particle Cloud will let your Photon device share up to 20 cloud variables at one time. Each of your cloud variables in Particle Cloud has to be given a unique name \(up to 12 characters in length\).

If your Photon device app needs to share **multiple** variables, use a separate `Particle.variable()` statement for each device variable being shared.

## Web App JS

particle.getVariable\(\)



