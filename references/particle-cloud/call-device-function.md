# Call Device Function

Your Photon device app can share a custom function through Particle Cloud, so your web app can call the function to make it run on your Photon device.

For example, your Photon device app could share a custom function that toggles an LED light on or off, so your web app would be able to call this function to turn the light on or off.

![](../../.gitbook/assets/particle-cloud-function.png)

Your Photon device app will use the `Particle.function()` method to share a custom function through Particle Cloud.

A "cloud function" will be created that acts like a reference to the custom function in your device app.

Your web app will use the `particle.callFunction()` method to make the custom function run on your Photon device.

## Photon Device App

Your Photon device app will use the `Particle.function()` method to share a custom function through Particle Cloud by creating a cloud function.  In addition, you will also need to modify the custom function to work with Particle Cloud.

### Share Device Function

Add this code statement \(**be sure to modify**\) within the `setup()` function of your Photon app:

```cpp
Particle.function("myFunction", myFunction);
```

The `Particle.function()` method requires two parameters inside its parentheses \(in this order\):

1. **The cloud function name**, which can be up to 12 characters in length. If possible \(for simplicity\), make your cloud function name match your device function name. However, the cloud function is allowed to have a different name. The cloud function name must be listed within double quotation marks. Change `"myFunction"` to the actual name that you want to use for the cloud function.
2. **The Photon device function name**, which is the custom function in your Photon device app that will be shared through Particle Cloud. Change `myFunction` to the actual name of the custom function in your Photon device app that you want to share.

Particle Cloud will let your Photon device share up to 15 cloud functions at one time. Each of your cloud functions in Particle Cloud has to be given a unique name \(up to 12 characters in length\).

If your Photon device app needs to share **multiple** functions, use a separate `Particle.function()` statement for each device function being shared.

### Modify Device Function

In order to share a custom function in your Photon device app with Particle Cloud, the custom function **must** be modified to do the following:

* The custom function must **accept a String parameter** when the function is called.
* The custom function must **return an integer value** when the function is performed.

For example, a typical custom function in your device app would have this generic format:

```cpp
void myFunction() {
    // code statements to be performed by function
}
```

The code for this custom function would need to be modified to accept a String parameter \(i.e., text\) and return an integer value \(i.e., whole number\). Here's a modified version of the function:

```cpp
int myFunction(String data) {
    // code statements to be performed by function
    return 1;
}
```

Here are the 3 modifications that you would make:

1. `String data` is now listed inside the parentheses after the function name. This represents the parameter that the function will accept: `String` is the data type for the parameter \(i.e., text\) , and `data` is the name of a local variable that will receive and store the parameter value \(text string\). If desired, you could use a different variable name other than `data`.
2. `int` is now listed in front of the function name \(instead of `void`\), which indicates the function will return an integer value \(whole number\).
3. The code statement `return 1;` was included inside the function \(at the end before the closing curly brace\), which will return an integer value of 1.

{% hint style="success" %}
**IMPORTANT:**  Your custom function **must** have these modifications – even if your custom function doesn't do anything with the text passed into the `data` parameter – and even if your device app doesn't do anything with the integer value returned by the custom function.
{% endhint %}

### Calling Device Function

Once a custom function in your Photon device app has been modified to be shared through Particle Cloud, your Photon app and your web app **must** include a text parameter when calling the function.

If the custom function **doesn't** actually do anything with the parameter, then this text string parameter can be **any text** – even an empty text string of `""` will work.

For example, in your Photon app, a code statement to call the custom function would be:

```cpp
myFunction("text");
```

* `myFunction` represents the name of the custom function. Change this to the name of your custom function.
* `"text"` represents the text string being passed into the function as a parameter. If this text parameter is not actually used within the function, then it can be any text string enclosed within double quotation marks – even an empty text string of `""` will work.

### Using String Parameter

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

For example, imagine your Photon device had a green button and a red button to control the LED:  pressing the green button will turn on the LED, and pressing the red button will turn off the LED. The code in your `loop()` function might look like this:

```cpp
void loop() {
    int greenButtonState = digitalRead(greenButton);
    int redButtonState = digitalRead(redButton);
    
    if(greenButtonState == LOW) {
        turnLight("on");
    }
    else if(redButtonState == LOW) {
        turnLight("off");
    }
}
```

## Web App JS

particle.callFunction\(\)



