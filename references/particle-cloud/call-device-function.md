# Call Device Function

Your Photon device app can share a custom function through Particle Cloud, so your web app can call the function to make it run on your Photon device.

For example, your Photon device app could share a custom function that toggles an LED light on or off, so your web app would be able to call this function to remotely turn the light on or off.

![](../../.gitbook/assets/particle-cloud-function.png)

Your Photon device app will use the `Particle.function()` method to share a custom function through Particle Cloud.

A "cloud function" will be created that acts like a reference to the custom function in your device app.

Your web app will use the `particle.callFunction()` method to make the custom function run on your Photon device by calling its cloud function reference.

## Photon Device App

Your Photon device app will use the `Particle.function()` method to share a custom function through Particle Cloud by creating a cloud function.  In addition, you will also need to modify the custom function to work with Particle Cloud.

### Share Device Function

Add this code statement \(**be sure to modify**\) within the `setup()` function of your Photon app:

```cpp
Particle.function("cloudFunc", deviceFunc);
```

The `Particle.function()` method requires two parameters inside its parentheses \(in this order\):

1. **The cloud function name**, which can be up to 12 characters in length. If possible \(for simplicity\), make your cloud function name match your device function name. However, the cloud function is allowed to have a different name. The cloud function name must be listed within double quotation marks. Change `"cloudFunc"` to the actual name that you want to use for the cloud function.
2. **The Photon device function name**, which is the custom function in your Photon device app that will be shared through Particle Cloud. Change `deviceFunc` to the actual name of the custom function in your Photon device app that you want to share.

Particle Cloud will let your Photon device share up to 15 cloud functions at one time. Each of your cloud functions in Particle Cloud has to be given a unique name \(up to 12 characters in length\).

If your Photon device app needs to share **multiple** functions, use a separate `Particle.function()` statement for each device function being shared.

### Modify Device Function

In order to share a custom function in your Photon device app with Particle Cloud, the custom function **must** be modified to do the following:

* The custom function must **accept a String parameter** when the function is called.
* The custom function must **return an integer value** when the function is performed.

For example, a typical custom function in your device app would have this generic format:

```cpp
void deviceFunc() {
    // code statements to be performed by function
}
```

The code for this custom function would need to be modified to accept a String parameter \(i.e., text\) and return an integer value \(i.e., whole number\). Here's a modified version of the function:

```cpp
int deviceFunc(String data) {
    // code statements to be performed by function
    return 1;
}
```

Here are the 3 modifications that were made to the custom function:

1. `String data` is listed inside the parentheses after the function name. This represents the parameter that the function will accept: `String` is the data type for the parameter \(i.e., text\) , and `data` is the name of a local variable that will receive and store the parameter value \(text string\). If desired, you could use a different variable name other than `data`.
2. `int` is listed in front of the function name \(instead of `void`\), which indicates the function will return an integer value \(whole number\).
3. The code statement `return 1;` is included inside the function \(at the end before the closing curly brace\), which will return an integer value of 1. This is the simplest way to have the function return a value. 

{% hint style="success" %}
**IMPORTANT:**  Your custom function **must** have these modifications – even if your custom function doesn't do anything with the text passed into the `data` parameter – and even if your device app doesn't do anything with the integer value returned by the custom function.
{% endhint %}

### Calling Device Function

Once a custom function in your Photon device app has been modified to be shared through Particle Cloud, your Photon app \(and your web app\) **must** include a text parameter when calling the function.

If the custom function **doesn't** actually do anything with the parameter, then this text string parameter can be **any text** – even an empty text string of `""` will work.

For example, in your Photon app, a code statement to call the custom function would be:

```cpp
deviceFunc("text");
```

* `deviceFunction` represents the name of the custom function. Change this to the name of your custom function.
* `"text"` represents the text string being passed into the function as a parameter. If this text parameter isn't actually used within the function, then it can be any text string enclosed within double quotation marks – even an empty text string of `""` will work.

### Using String Parameter

As stated previously, the Photon device function being shared through Particle Cloud must accept a String parameter. The function doesn't actually have to do anything with this text data \(other than receive it when the function is called\).

However, depending on what your custom function does, the text string passed into the `data` parameter could be used to decide what action\(s\) are performed within the custom function.

For example, imagine you created a custom function named `turnLight()` to turn an LED light either on or off based on the value of a text string passed into the function as a parameter:

```cpp
int turnLight(String data) {
    if(data == "on")
        digitalWrite(LED, HIGH);
    }
    else if(data == "off") {
        digitalWrite(LED, LOW);
    }
    return 1;
}
```

To turn on the LED, your Photon app \(or your web app\) would call `turnLight()` and include`"on"` as the parameter. In your Photon app, the code statement would be:  `turnLight("on");`

To turn off the LED, your Photon app \(or your web app\) would call `turnLight()` function and include `"off"` as the parameter. In your Photon app, the code statement would be:  `turnLight("off");`

## Web App JS

Your web app JS will use the `particle.callFunction()` method to make a custom function run on your Photon device by calling its cloud function reference in Particle Cloud.

Add this code \(**be sure to modify**\) in your web app JS:

```javascript
function webFunction() {
    particle.callFunction({ deviceId: myDevice, name: "cloudFunc", argument: "text", auth: myToken });
}
```

{% hint style="success" %}
**MODIFY CODE:**  You will need to make these changes to the example code above:

1. Change `webFunction()` to the name you want to use for your custom function
2. Change `"cloudFunc"` to the name of your cloud function you want to call
3. If necessary, change `"text"` to a different text parameter – only necessary if your Photon device function uses the text parameter to decide what actions are performed.
{% endhint %}

This code adds a custom function named `webFunction()` to your web app JS.  This custom function contains the `particle.callFunction()` method.

Be sure to change `webFunction()` to the actual name that you want to use for this JS function. If helpful, you could use the same name as the Photon device function being called. For example, if the JS function is supposed to call a function named `toggleLight()` in your Photon device app, you could also name the JS function as `toggleLight()`.

The `particle.callFunction()` method requires your Photon device ID, the name of your cloud function, an argument \(a String parameter for the Photon function\), and your Photon access token:

1. `myDevice` is a global variable in your web app JS that should store your Photon device ID
2. `"cloudFunc"` is the name of your cloud function, which must be listed inside double quotation marks. Be sure to change `"cloudFunc"` to the actual name of your cloud function.
3. `"text"` is the String parameter that will be passed into the Photon device function. If this text parameter isn't actually used within the Photon function, then it can be any text string enclosed within double quotation marks – even an empty text string of `""` will work.
4. `myToken` is a global variable in your web app JS that should store your Photon access token

### Calling JS Function

Your web app will need a way to call the JS function which contains the `particle.callFunction()` method that makes a function run on your Photon device.

One common way to do this is to add a button in your web app HTML that can be clicked by the user. The button will have an [onclick event](https://www.w3schools.com/jsref/event_onclick.asp) that will call the JS function \(which will call the Photon function\).

Add this to your web app HTML file **within** the `<body>` section where you want the button to appear:

```markup
<button onclick="webFunction()">Button Label</button>
```

* Change `webFunction()` to the name of the JS function to be called when the button is clicked. This should be a JS function that contains a `particle.callFunction()` method.
* Change `Button Label` to whatever text you want displayed in the button as its label.



