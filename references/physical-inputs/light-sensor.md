# Light Sensor

The Photon kit includes a light sensor \(also known as a **photocell**\) which is a variable resistor that changes its resistance in response to the amount of ambient light in the environment.

![Light Sensor \(aka Photocell\)](../../.gitbook/assets/photocell.jpg)

For example, some outdoor lights on houses and buildings use photocells to automatically turn the light on or off depending on whether it is dark or light outside. Most smartphones have light sensors to automatically adjust the brightness of the screen depending on the amount of ambient light detected.

## How to Connect Light Sensor

The light sensor is a **variable** resistor:  its resistance changes \(depending on the amount of light it is exposed to\).  A **static** resistor \(which has a fixed resistance\) will be connected in series with the photocell to create a [voltage divider](https://learn.sparkfun.com/tutorials/voltage-dividers). This will allow the Photon to measure the resistance of the photocell, which indicates the amount of light reaching the sensor.

### Bend Resistor Legs

A static resistor will be used to connect one leg of the light sensor to a GND \(-\) pin.

Your Photon kit contains a set of resistors with a resistance rating of 330 Ohms. In order to insert a resistor into the pin holes of a breadboard, you will need to bend both resistor legs into ~90° angles:

![Bending Resistor Legs](../../.gitbook/assets/resistor-bend-legs.png)

### Connect to Breadboard

The light sensor has 2 metal legs that will be inserted into pin holes on the breadboard. One of the legs will actually have **two** connections – this is the voltage divider created using a static resistor.

To connect a light sensor to your Photon using the breadboard, you will need:

* Light sensor \(aka photocell\)
* Resistor with bent legs
* 2 jumper wires \(use different colors to help identify them\)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Light Sensor (Photocell)</th>
      <th style="text-align:left">Photon Pin</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">First Leg (either one)</td>
      <td style="text-align:left">3.3V</td>
    </tr>
    <tr>
      <td style="text-align:left">Second Leg</td>
      <td style="text-align:left">
        <p>(1) any analog I/O pin (A0, A1, A2, A3, A4, A5)</p>
        <p>(2) GND using resistor</p>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="success" %}
**3.3V MAXIMUM:**  Analog inputs, such as the light sensor, require 3.3V of power for accurate measurements. Connect the light sensor to the 3.3V pin on your Photon, or connect it to a positive power rail that's connected to the 3.3V pin.
{% endhint %}

{% hint style="success" %}
**RESISTOR REQUIRED:** A static resistor will be used to create a voltage divider that allows the variable resistance of the light sensor to be measured.
{% endhint %}

{% hint style="warning" %}
**TWIN PINS:** Analog pins A2, A3, A4, and A5 are each represented by **two** pins on the Photon board. The duplicate pins are labeled as: SS/A2, SCK/A3, MISO/A4, MOSI/A5. If you use one of these pins, you **cannot** use its twin at the same time.
{% endhint %}

Here are the steps to connect the light sensor to your Photon using the breadboard:

1. Insert the two legs of the light sensor into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as **one sensor leg**. Plug the other end of this jumper wire into the 3.3V pin on the Photon circuit board \(or plug it into a positive power rail that's connected to the 3.3V pin via a different jumper wire\).
3. Plug one end of a **second jumper wire** into the same terminal strip row as the **second sensor leg**. Plug the other end of this jumper wire into any analog I/O pin on the Photon circuit board.
4. Insert one end of the **resistor** into the **same** terminal strip row as the **second sensor leg**. Insert the other end of the resistor into a pin hole of the negative column of the closest power rail on the breadboard.
5. If the negative power rail isn't already connected to a GND pin on the Photon circuit board, then plug one end of a third jumper wire into another pin hole in the negative power rail, and plug the other end of this jumper wire into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a light sensor \(ignore the wiring at the top for the temperature sensor\):

![](../../.gitbook/assets/experiment-6.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your light sensor legs could be inserted into **different row numbers** on the breadboard. \(The example connects the legs to row 27 and row 30.\)
* Your light sensor legs could be inserted into a **different column** on the breadboard. \(The example connects the legs into column F of the terminal strip rows.\)
* Your light sensor could connect to a **different analog I/O pin**. \(The example connects to the A0 pin.\)
* Your light sensor could connect \(through a jumper wire\) **either directly to the 3.3V pin** **or to a positive power rail on the breadboard that's connected to the 3.3V pin.**
* The negative power rail on your breadboard could connect to a **different GND pin**. \(There are three available GND pins.\)

## How to Code Light Sensor

The basic steps to control a light sensor \(photocell\) in your app code are:

1. Declare a global variable to store the I/O pin number for the light sensor.
2. Use the `analogRead()` method to measure the amount of light.
3. **OPTIONAL:**  Use the `map()` method to convert the sensor reading to a custom range.

### Global Variable

You should declare a global variable to store the I/O pin number that the light sensor is connected to. This will make it easier to understand your code \(and easier to modify the code if you were to connect the trimpot to a different pin number\).

Add this code statement \(modify if necessary\) **before** the `setup()` function:

```cpp
int light = A0;
```

This line of code does 3 things \(in order\):

1. **It declares a data type for the variable's value.**  In this case, `int` stands for integer \(whole number\). Photon pin numbers are always treated as `int` values \(even though they have letters\).
2. **It declares the variable's name.** In this example, the variable will be called `light`. You can change the variable name, but choose a name that will make sense to anyone reading the code.
3. **It assigns a value to the variable.**  In this example, the variable's value will be equal to `A0`. If necessary, modify this value to match the actual I/O pin that your speaker is connected to.

{% hint style="info" %}
**PIN MODE:**  Analog inputs do **NOT** need to have their pin mode set within the `setup()` function. Their pin mode gets automatically set when the `analogRead()` method is used.
{% endhint %}

### Read Light Sensor

The `analogRead()` method is used to read the light sensor, which indicates the amount of ambient light reaching the sensor.

Add this code \(modify as necessary\) to your app within the `loop()` function or a custom function:

```cpp
int lightRead = analogRead(light);
// add code to do something with lightValue
```

A local variable named `lightRead` is declared that will have a data type of `int` \(integer\).  This variable is made equal to whatever value is returned by the `analogRead()` method.  You can change the name of this variable, but it will make sense if it's similar to the variable name used for the trimpot pin number.

The `analogRead()` method requires one parameter insides its parentheses: 

1. **The I/O pin number**, which can be the actual pin number \(such as: `A0`, etc.\) or a variable that stores a pin number. In this example, the variable named `light` is listed. If necessary, change this to match the variable name for your trimpot's pin number.

The `analogRead()` method will return an integer \(whole number\) value ranging from 0-4095:

* When there is **less light** detected, the reading will have a **lower value**.
* When there is **more light** detected, the reading will have a **higher value**.

You'll need to add code to do something with the reading stored as `lightRead`. For example, this might be an if-else statement to perform certain actions based on whether `lightRead` is greater than \(or less than\) one or more specific values.

#### GATHER TEST VALUES

Depending on the specific purpose of the light sensor in your device, you may need to gather some test values under different conditions to see how dark or how bright the environment will actually be where your device will be used. This will help you determine which values to use in your code to make decisions. For example, if the light sensor will be used to turn on an LED light when a room is too dark, what value will be used to decide that the room is too dark?

For example, the code below uses a value of `250` to decide whether a room is too dark. However, you would need to gather test data to determine whether this value should be higher or lower.

```cpp
if (lightRead < 250) {
    // turn on LED when room is too dark
    digitalWrite(LED, HIGH);
}
else {
    // otherwise, turn off LED
    digitalWrite(LED, LOW);
}
```

### Map Value to Custom Range <a id="mapping-dial-position-to-custom-range-of-values"></a>

In many cases, it may not be convenient to work with a value that ranges from 0-4095. Instead, it might be easier to have a value within a smaller custom range \(such as:  0-10, 0-100, etc.\) that makes more sense for your particular task.

The `map()` function can be used to convert a value from its original range \(such as 0-4095\) into a new range of your choice. You decide the minimum and maximum values for the new range.

For example, if the light sensor were being used to automatically turn on an LED light when the environment is too dark, you might want the sensor to return a value between 0-100 as an easier way to determine the relative brightness of the environment.

Add this code \(modify as necessary\) to your app within the `loop()` function or a custom function:

```cpp
int lightRead = analogRead(light);
int minValue = 0;
int maxValue = 100;
int lightValue = round(map(lightRead, 0, 4095, minValue, maxValue + 1));
// add code to do something with lightValue
```

As necessary, change the values assigned to `minValue` and `maxValue` to whatever numbers you want to use for your custom range. Also, the `minValue` **doesn't** have to be zero.

Be sure to add code to do something with `lightValue`. For example, this might be an if-else statement to perform certain actions based on whether `lightValue` is greater than \(or less than\) one or more specific values.

**NOTE:** The code uses the `round()` method to round the mapped value to the nearest integer because the `map()` method returns a `float` \(decimal value\). Also, inside the `map()` method, the code intentionally adds 1 to the `maxValue` because otherwise it is very difficult to get the maximum value even if the ambient light in the environment is very bright.

#### CUSTOM FUNCTION TO READ ANALOG SENSORS

You could incorporate this code into a custom function called `checkSensor()` that will read an analog sensor and return a value mapped to a custom range:

```cpp
int checkSensor(int pin, int minValue, int maxValue) {
    int sensorRead = analogRead(pin);
    int mapValue = round(map(sensorRead, 0, 4095, minValue, maxValue + 1));
    return mapValue;
}
```

When calling the `checkSensor()` function within the `loop()` function, you will need to include values for these 3 parameters \(in order\) inside its parentheses:

1. the **sensor's pin number**, which will most likely be a variable that stores the pin number
2. the **desired minimum value for the range**, which should be an integer \(whole number\)
3. the **desired maximum value for the range**, which should be an integer \(whole number\)

The `checkSensor()` function will return the mapped sensor value as an integer, which your code should store in a variable of data type `int`.

For example, to call the `checkSensor()` function within the `loop()` function:

```cpp
int lightValue = checkSensor(light, 0, 100);
// add code to do something with lightValue
```

The `checkSensor()` function could also be used to read other analog sensors, such as a trimpot dial:

```cpp
int trimpotValue = checkSensor(trimpot, 0, 255);
// add code to do something with trimpotValue
```

