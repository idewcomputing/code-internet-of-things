# Read Device Variable

Your Photon device app can share a variable through Particle Cloud, so your web app can read the value of the variable.

For example, your Photon device could measure the temperature of a room using a sensor, store the measurement in a variable, and share this variable through Particle Cloud, so your web app can read the variable's value and display it.

![](../../.gitbook/assets/particle-cloud-variable.png)

Your Photon device app will use the `Particle.variable()` function to share the value of a device variable through Particle Cloud.

A "cloud variable" will be created to store the value of your device variable. Whenever the value of your device variable changes, the value stored in the cloud variable will be automatically synced to match.

Your web app will use the `particle.getVariable()` function to read the value of your cloud variable.

## Photon Device App

Your Photon device app will use the `Particle.variable()` function to share the value of a device variable through Particle Cloud by creating a cloud variable.

Add this code statement \(**be sure to modify**\) within the `setup()` function of your Photon app:

```cpp
Particle.variable("myVariable", myVariable);
```

The Particle.variable\(\) function requires two parameters inside its parentheses \(in this order\):

1. **The cloud variable name**, which can be up to 12 characters in length. If possible \(for simplicity\), make your cloud variable name match your device variable name. However, the cloud variable is allowed to have a different name. The cloud variable name must be listed within double quotation marks. Change `"myVariable"` to the actual name that you want to use for the cloud variable.
2. **The Photon device variable name**, which is the variable in your Photon device app whose value will be shared in Particle Cloud. Change `myVariable` to the actual name of the variable in your Photon device app that you want to share.

**NOTE:** The only data types that are allowed to be shared as cloud variables are:

* `int` \(whole numbers\)
* `double` \(decimal numbers\)
* `String` \(text, up to 622 characters\)

Particle Cloud will let your Photon device share up to 20 cloud variables at one time. Each of your cloud variables in Particle Cloud has to be given a unique name \(up to 12 characters in length\).

If your Photon device app needs to share **multiple** variables, use a separate `Particle.variable()` statement for each device variable being shared.

## Web App JS

Your web app JS will use the `particle.getVariable()` function to read the value of a Photon device variable stored as a cloud variable in Particle Cloud.

Add this code for a custom function \(**be sure to modify**\) in your web app JS:

```javascript
function myFunction() {
    particle.getVariable({ deviceId: myDevice, name: "myVariable", auth: myToken }).then(function(data) {
        // add code to do something with value returned as data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });
}
```

{% hint style="success" %}
**MODIFY CODE:**  You will need to make changes in this code example:

1. Change `myFunction()` to the name you want to use for your custom function
2. Change `"myVariable"` to the name of your cloud variable whose value you want
3. Add code to do something with the value returned as `data.body.result`
{% endhint %}

This code adds a custom function named `myFunction()` to your web app JS.  This custom function contains the `particle.getVariable()` function \(which will contain code that you'll add to do something with the variable value returned by Particle Cloud\).

Be sure to change `myFunction()` to the name that you want to use for your custom function.  For example, if you were getting the value of a temperature variable from your Photon device, you might name the function `getTemperature()`.

The `particle.getVariable()` function requires your Photon device ID, the name of your cloud variable, and your Photon access token:

1. `myDevice` is a global variable in your web app JS that should store your Photon device ID
2. `"myVariable"` is the name of your cloud variable, which must be listed inside double quotation marks. Be sure to change `"myVariable"` to the actual name of your cloud variable.
3. `myToken` is a global variable in your web app JS that should store your Photon access token

When Particle Cloud returns the value of your cloud variable, this value gets temporarily stored in a local variable called: `data.body.result`

You will need to add code within the particle.getVariable\(\) function to do something with the value stored in `data.body.result`. For example, you could add code to:

* Display the value in your web app \(by using jQuery to modify the HTML\)
* Change the style of your web app based on the value \(by using jQuery to modify the CSS\)
* Save the value in your web app \(by assigning the value to a JS global variable\)



