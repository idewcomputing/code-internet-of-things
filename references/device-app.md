# Photon Device App

All the apps that run on your Photon device will be coded using Particle's version of the open-source [Wiring](http://www.wiring.org.co/reference/) programming language framework for microcontrollers.

The [Particle firmware](https://docs.particle.io/reference/firmware/photon/) on your Photon runs a modified version of the Wiring language with a few minor differences, as well as some additional methods \(functions\) customized for the Photon hardware.

{% hint style="info" %}
**WIRING VS. ARDUINO:** [Arduino](https://www.arduino.cc/reference/en/) is another programming language framework for microcontrollers. It turns out that Arduino is based on Wiring, so the two languages are nearly identical \(though there are some differences\). In most cases, a program originally written in Arduino will work on your Photon with only minor revisions. So once you've learned how to program in one of these languages, you've basically learned both.
{% endhint %}

{% hint style="info" %}
**WIRING VS. C++:** Wiring \(like Arduino\) is a programming framework written in C++, so you can also directly incorporate C++ code within your device app.
{% endhint %}

## Photon App Template

When you create a new device app in [Particle Build](particle-build.md), a basic app template is provided that consists of an empty `setup()` function and an empty `loop()` function:

```cpp
void setup() {​

}

​void loop() {​

}
```

If you want an app template that provides more guidance, you can replace the default app template with the code below, which has some comments to explain each major section of your app:

```cpp
/*
Team Name
App Title
*/

// global variables - store pin numbers and other data used in functions


// setup() function runs one time when app first starts - set pin modes, etc.
void setup() {

}

// after setup() finishes, loop() function runs repeatedly - main tasks of app
void loop() {

}

// custom functions - tasks or subtasks usually called within loop() function

```

{% hint style="success" %}
**COPY CODE:** When using this IoT code guidebook, you can copy a code block simply by clicking the **copy icon** displayed in the upper right of the code block.
{% endhint %}

### Setup Function

Every Photon device app must have one \(and only one\) `setup()` function.  You can add lines of code between this function's opening and closing curly braces.

The `setup()` function will run **one time** when your app first starts \(which is when your Photon is first powered on – or is restarted using its Reset button\).

The code added within the `setup()` function typically sets pin modes for the device's inputs and outputs, initializes settings for certain inputs and outputs, or performs other "setup" actions that need to occur at the start of the program.

Even if you didn't add any code within the `setup()` function, your app must still have this function.

### Loop Function

Every Photon device app must have one \(and only one\) `loop()` function.  You can add lines of code between this function's opening and closing curly braces.

After the `setup()` function is done running, the `loop()` function will start to run. When all the code within the `loop()` function has been performed, the `loop()` function will automatically run itself again. It keeps running in an **endless loop** \(until the device is restarted or powered off\).

The code added within the `loop()` function performs the main tasks of your program.

Even if you didn't add any code within the `loop()` function, your app must still have this function.

{% hint style="info" %}
**VOID:**  Why is [`void`](http://www.wiring.org.co/reference/void.html) listed before the `setup()` and `loop()` functions?  This is because each function in your Photon device app must declare a data type \(such as: integer, boolean, etc.\) for the data value returned by the function. In this case, `void` indicates the function does **NOT** return any data value.
{% endhint %}

## Other Sections of App

Besides having the required `setup()` and `loop()` functions, your Photon device apps will typically have some or all of the following:

* Comments
* Libraries
* Global Variables
* Custom Functions

### Comments

Comments are optional notes that you can insert to help explain or clarify portions of the code to anyone reviewing the program. Comments can be [single-line](http://www.wiring.org.co/reference/comment.html) or [multi-line blocks](http://www.wiring.org.co/reference/multilinecomment.html). 

It's a good idea to have at least one comment at the beginning of your app code to provide a name and/or description of your app.

Any comments in your app are ignored when the program is compiled and uploaded to your device.

```cpp
// Comments are notes to yourself or others reading your code
// Each single-line comment starts with two forward slashes
​
/*
A multi-line comment block starts with a forward slash and asterisk
You can include as many lines of notes in the block as you need
A multi-line comment block ends with an asterisk and forward slash
*/
```

### Libraries

Some device apps might include \(i.e., import\) one or more library files. A library is a file of pre-built code that provides additional functions that your program can utilize. For example, certain inputs and outputs have their own code library with functions to make it easier to control the input or output.

Particle Build has a **Libraries** menu where you can search for existing libraries \(or upload your own library file that you've created\). When you select a library to be added to your app, Particle Build will automatically insert an [`#include`](http://www.wiring.org.co/reference/include.html) statement for the library at the beginning of your app code.

### Global Variables

Your device app will typically have code that declares global variables which store data used in your program's functions, such as pin numbers for sensors, etc.

Global variables are usually listed before the `setup()` function \(to make it easier to read the code\).

### Custom Functions

You can also add your own custom functions to your device app. Each custom function must have a unique function name.

Custom functions are typically used to contain code that performs specific tasks or subtasks. Having custom functions in your app is optional, but they can help break up your code into smaller modules that are easier to understand \(and easier to re-use\). So rather than listing all your main program code within the `loop()` function, you can subdivide some or all of the code into custom functions.

The code within a custom function is only run if and when that custom function is "called" \(by listing the function's name\) within the `setup()` or `loop()` function. A custom function can also be "called" within another custom function.

Custom functions are usually listed after the `loop()` function \(to make it easier to read the code\).

## Resources

If you want to learn more about programming your Photon device, consult these references:

* [Wiring Programming Reference](http://www.wiring.org.co/reference/)
* [Particle Firmware Reference](https://docs.particle.io/reference/firmware/photon/)



