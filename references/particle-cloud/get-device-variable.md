# Get Device Variable

Your Photon device app can share a variable through Particle Cloud, so your web app can get the value of the variable.

For example, your Photon device app could measure the temperature of a room using a sensor, store the measurement in a variable, and share this variable's value through Particle Cloud, so your web app can get the variable's value and display it.

![](../../.gitbook/assets/particle-cloud-variable.png)

Your Photon device app will use the `Particle.variable()` method to share the value of a device variable through Particle Cloud.

A "cloud variable" will be created to store the value of your device variable. Whenever the value of your device variable changes, the value stored in the cloud variable will be automatically synced to match.

Your web app will use the `particle.getVariable()` method to get the value of your cloud variable.

## Photon Device App

Your Photon device app will use the `Particle.variable()` method to share the value of a device variable through Particle Cloud by creating a cloud variable.

Add this code statement \(**be sure to modify**\) within the `setup()` function of your Photon app:

```cpp
Particle.variable("cloudVar", deviceVar);
```

The `Particle.variable()` method requires two parameters inside its parentheses \(in this order\):

1. **The cloud variable name**, which can be up to 12 characters in length. If possible \(for simplicity\), make your cloud variable name match your device variable name. However, the cloud variable is allowed to have a different name. The cloud variable name must be listed within double quotation marks. Change `"cloudVar"` to the actual name that you want to use for the cloud variable.
2. **The Photon device variable name**, which is the variable in your Photon device app whose value will be shared in Particle Cloud. Change `deviceVar` to the actual name of the variable in your Photon app that you want to share.

Particle Cloud will let your Photon device share up to 20 cloud variables at one time. Each of your cloud variables in Particle Cloud has to be given a unique name \(up to 12 characters in length\).

If your Photon device app needs to share **multiple** variables, use a separate `Particle.variable()` statement for each device variable being shared.

### Allowed Data Types

**NOTE:** The only data types that are allowed to be shared as cloud variables are:

* `int` \(whole numbers\)
* `double` \(decimal numbers\)
* `String` \(text, up to 622 characters\)

Be sure each Photon device variable being shared as a cloud variable uses one of these data types.

## Web App JS

Your web app JS will use the `particle.getVariable()` method to get the value of a Photon device variable stored as a cloud variable in Particle Cloud.

Add this code \(**be sure to modify**\) in your web app JS:

```javascript
function webFunction() {
    particle.getVariable({ deviceId: myDevice, name: "cloudVar", auth: myToken }).then(function(data) {
        // add code to do something with value returned as: data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });
}
```

{% hint style="success" %}
**MODIFY CODE:**  You will need to make these changes to the example code above:

1. Change `webFunction()` to the name you want to use for your custom function
2. Change `"cloudVar"` to the name of your cloud variable whose value you want
3. Add code inside the `particle.getVariable()` method to do something with the variable value returned as: `data.body.result`
{% endhint %}

This code adds a custom function named `webFunction()` to your web app JS.  This custom function contains a call to the `particle.getVariable()` method, which will also contain code you'll add to perform action\(s\) based on the variable value returned by Particle Cloud.

Be sure to change `webFunction()` to the actual name that you want to use for this JS function.  For example, if the function is supposed to get the value of a temperature variable from your Photon device, you might name the function something like: `getTemperature()`

The `particle.getVariable()` method requires your Photon device ID, the name of your cloud variable, and your Photon access token:

1. `myDevice` is a global variable in your web app JS that should store your Photon device ID
2. `"cloudVar"` is the name of your cloud variable, which must be listed inside double quotation marks. Be sure to change `"cloudVar"` to the actual name of your cloud variable.
3. `myToken` is a global variable in your web app JS that should store your Photon access token

When Particle Cloud returns the value of your cloud variable, this value gets temporarily stored in a local variable called: `data.body.result`

You will need to add code within the `particle.getVariable()` method to do something with the value stored in `data.body.result`.

For example, you could add code to:

* Display the value in your web app \(by using jQuery to modify the HTML\)
* Change the style of your web app based on the value \(by using jQuery to modify the CSS\)
* Save the value in your web app \(by assigning the value to a JS global variable\)

### Set Interval to Get Variable

If your web app needs to continuously monitor the value of a cloud variable, you can use the `window.setInterval()` method to automatically call \(perform\) a function at a set time interval \(such as every 0.5 seconds, etc.\).

Add this code statement \(**be sure to modify**\) near the top of your web app JS:

```javascript
window.setInterval(webFunction, 2000);
```

The `window.setInterval()` method requires two parameters inside its parentheses \(in this order\):

1. **The name of the function to be called**, which will be the name of the custom function in your JS  that contains the `particle.getVariable()` method for the variable you need to continuously monitor. The custom function's name should be listed **without** a set of parentheses. Change `webFunction` to the name of your custom function.
2. **The time interval between calls**, which will be the amount of time between each call to the function. The time interval is specified in milliseconds \(1000 ms = 1 second\). In this case, the interval was set to `2000` ms \(2 seconds\). Change this value to an appropriate time interval for your web app.

### Getting Multiple Variables

If you want to get the values of **multiple** cloud variables at the **same time**, you can include separate calls to the `particle.getVariable()` method within the same custom function:

```javascript
function webFunction() {
    // get 1st variable
    particle.getVariable({ deviceId: myDevice, name: "cloudVar1", auth: myToken }).then(function(data) {
        // add code to do something with value returned as: data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });

    // get 2nd variable
    particle.getVariable({ deviceId: myDevice, name: "cloudVar2", auth: myToken }).then(function(data) {
        // add code to do something with value returned as: data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });
}
```

If your web app needs to get different cloud variables at **different times**, then create separate custom functions to get each cloud variable individually:

```javascript
function webFunction1() {
    particle.getVariable({ deviceId: myDevice, name: "cloudVar1", auth: myToken }).then(function(data) {
        // add code to do something with value returned as: data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });
}

function webFunction2() {
    particle.getVariable({ deviceId: myDevice, name: "cloudVar2", auth: myToken }).then(function(data) {
        // add code to do something with value returned as: data.body.result
        
        
    }, function(err) {
        console.log("An error occurred:", err);
    });
}

```

