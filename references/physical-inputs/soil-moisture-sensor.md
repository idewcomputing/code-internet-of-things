# Soil Moisture Sensor

The soil moisture sensor in your Photon kit can be inserted into soil or similar materials \(sand, etc.\) to measure the amount of moisture in the material.

![Soil Moisture Sensor](../../.gitbook/assets/moisture-sensor.jpg)

## How to Connect Moisture Sensor

The moisture sensor is a variable resistor with two gold-plated legs that are inserted into soil. Moisture in the soil will conduct electricity from one sensor leg to the other. The amount of electricity conducted  depends on the amount of soil moisture.

### Attach Wires to Sensor

The soil moisture sensor in your Photo kit has a 3-pin screw terminal. You'll need to attach 3 jumper wires to the screw terminal. The back of the sensor has labels for the 3 pins:  SIG, GND, VCC.

To attach jumper wires to the soil moisture sensor, you will need:

* Soil moisture sensor with 3-pin screw terminal
* 3 jumper wires \(use different colors to help identify them; **recommend red, black, and yellow**\)
* Small flat-head screwdriver \(obtain from teacher, if necessary\)

1. Use a small flat-head screwdriver to turn each screw counterclockwise until slightly loosened \(but don't remove them\). This creates openings on the top of the terminal to insert the jumper wires.
2. Insert one end of the **first jumper wire \(yellow\)** into the terminal slot for **SIG**. Then use the screwdriver tighten that terminal's screw \(turn clockwise\) until the jumper wire is held firmly.
3. Insert one end of the **second jumper wire \(black\)** into the terminal slot for **GND**. Then use the screwdriver tighten that terminal's screw \(turn clockwise\) until the jumper wire is held firmly.
4. Insert one end of the **third jumper wire \(red\)** into the terminal slot for **VCC**. Then use the screwdriver tighten that terminal's screw \(turn clockwise\) until the jumper wire is held firmly.

![Jumper Wires Connected to Screw Terminal](../../.gitbook/assets/moisture-sensor-wires.jpg)

### Connect to Breadboard

To connect a soil moisture sensor to your Photon using the breadboard, you will need:

* Soil Moisture Sensor with 3 attached jumper wires

| Soil Moisture Sensor | Photon Pin |
| :--- | :--- |
| SIG \(Signal\) – Yellow | any analog I/O pin \(A0, A1, A2, A3, A4, A5\) |
| GND \(Ground\) – Black | GND |
| VCC \(Power\) – Red | any I/O pin |

{% hint style="info" %}
**DUAL I/O PINS:** The soil moisture sensor is connected to two different I/O pins. The sensor's SIG wire is connected to an analog I/O pin that will be used as an **input** to read data signals from the sensor. The sensor's VCC wire is connected to another I/O pin that will be used as an **output** to provide power to the sensor when taking a reading.
{% endhint %}

{% hint style="warning" %}
**TWIN PINS:** Analog pins A2, A3, A4, and A5 are each represented by **two** pins on the Photon board. The duplicate pins are labeled as: SS/A2, SCK/A3, MISO/A4, MOSI/A5. If you use one of these pins, you **cannot** use its twin at the same time.
{% endhint %}

Here are the steps to connect the soil moisture sensor to your Photon using the breadboard:

1. Plug the **SIG jumper wire** into any analog I/O pin on the Photon circuit board.
2. Plug the **GND jumper wire** into a pin hole connected to GND:  either plug it into a negative power rail on the breadboard \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.
3. Plug the **VCC jumper wire** into any I/O pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a soil moisture sensor:

![](../../.gitbook/assets/experiment-3.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your moisture sensor's SIG wire could connect to a **different analog I/O pin**. \(The example connects to the A2 pin on the Photon circuit board.\)
* Your moisture sensor's GND wire could connect **either to a different GND pin or to a negative power rail connected to a GND pin**. \(There are three available GND pins on the Photon circuit board.\)
* Your moisture sensor's VCC wire could connect to a **different I/O pin**. \(The example connects to the D6 pin on the Photon circuit board.\)
* Alternatively, you could connect the sensor's wires into different terminal strip rows on a breadboard, and then use additional jumper wires to connect to the Photon circuit board.

### Insert Sensor into Soil

Once the moisture sensor is connected to the Photon, insert the sensor legs into the soil \(or similar material\) where you need to take moisture measurements.

![Moisture Sensor Inserted into Soil of Potted Plant](../../.gitbook/assets/moisture-sensor-plant.jpg)

## How to Code Moisture Sensor

The basic steps to control a soil moisture sensor in your app code are:

1. Declare global variables to store the I/O pin numbers for the moisture sensor.
2. Set the pin mode for the sensor's power pin in the `setup()` function, and turn off the sensor.
3. Use a sequence of `digitalWrite()` and `analogRead()` statements to briefly turn on the sensor and read the soil moisture.
4. **OPTIONAL:**  Use the `map()` method to convert the sensor reading to a custom range.

### Global Variables

You should declare global variables to store the I/O pin numbers that the moisture sensor's SIG wire \(data signal\) and VCC wire \(power\) are connected to. This will make it easier to understand your code \(and easier to modify the code if you were to connect the trimpot to a different pin number\).

Add this code statement \(modify if necessary\) **before** the `setup()` function:

```cpp
int soil = A2;
int soilPower = D6;
```

Each line of code does 3 things \(in order\):

1. **It declares a data type for the variable's value.**  In this case, `int` stands for integer \(whole number\). Photon pin numbers are always treated as `int` values \(even though they have letters\).
2. **It declares the variable's name.** In this example, the variables will be called `soil` and `soilPower`. You can change the names, but choose names that will make sense to anyone reading the code.
3. **It assigns a value to the variable.**  In this example, `soil` will be equal to `A2` and `soilPower` will be equal to `D6`. If necessary, modify these values to match the actual I/O pins that your sensor's SIG and VCC wires are connected to.

### Set Pin Mode & Turn Off

You need to set the pin mode for the moisture sensor's power pin to be used as an output. Then you need turn off the power to the sensor until you're ready to actually take a sensor reading.

Add this code \(modify if necessary\) **within** the `setup()` function:

```cpp
pinMode(soilPower, OUTPUT);
digitalWrite(soilPower, LOW);
```

The `pinMode()` method requires two parameters inside its parentheses \(in this order\):

1. **The I/O pin number**, which can be the actual pin number \(such as: `D6`, etc.\) or a variable that stores a pin number. In this example, the variable named `soiPower` is listed. If necessary, change this to match the variable name for your moisture sensor's power pin.
2. **The mode value**, which will always be `OUTPUT` for an LED light because your app will send "on" and "off" signals \(or brightness signals\) to the LED light.

The `digitalWrite()` method requires two parameters inside its parentheses \(in this order\):

1. **The I/O pin number**, which can be the actual pin number \(such as: `D6`, etc.\) or a variable that stores a pin number. In this example, the variable named `soiPower` is listed. If necessary, change this to match the variable name for your moisture sensor's power pin.
2. **The signal value**, which can be `HIGH` or `LOW`. Your Photon uses this value to send an electrical signal through the pin: `HIGH` is a signal of 3.3 volts which represents "on," while `LOW` is a signal of 0 volts which represents "off." In this case, `LOW` is being used to turn off the moisture sensor.

{% hint style="info" %}
**PIN MODE:**  Analog inputs do **NOT** need to have their pin mode set within the `setup()` function. Their pin mode gets automatically set when the `analogRead()` method is used. That's why there's no `pinMode()` statement for the `soil` pin.
{% endhint %}

#### WHY TURN OFF POWER?

A constant flow of electricity across the moisture sensor legs could cause them to corrode over time due to the natural salts and other minerals found in soil. The gold-plating on the sensors legs resist corrosion, but it's still better to only briefly turn on the sensor's power when taking a reading.

### Read Moisture Sensor

Reading the soil moisture always requires a sequence of four steps:

1. Turn on the sensor's power using the `digitalWrite()` method.
2. Allow time for electricity to flow through the soil by using the `delay()` method.
3. Read the soil moisture using the `analogRead()` method.
4. Turn off the sensor's power using the `digitalWrite()` method.

```cpp
digitalWrite(soilPower, HIGH);
delay(10);
int soilRead = analogRead(soil);
digitalWrite(soilPower, LOW);​
// add code to do something based on value of soilRead
```

A local variable named `soilRead` is declared that will have a data type of `int` \(integer\). This variable is made equal to whatever value is returned by the `analogRead()` method. You can change the name of this variable, but it will make sense if it's similar to the variable name used for the trimpot pin number.

The `analogRead()` method requires one parameter insides its parentheses:

1. **The I/O pin number**, which can be the actual pin number \(such as: `A2`, etc.\) or a variable that stores a pin number. In this example, the variable named `soil` is listed. If necessary, change this to match the variable name for the pin number of your sensor's SIG wire.

The `analogRead()` method will return an integer \(whole number\) value ranging from 0-4095:

* When there is **less moisture** detected, the reading will have a **lower value**.
* When there is **more moisture** detected, the reading will have a **higher value**.

You'll need to add code to do something with the reading stored as `soilRead`. For example, this might be an if-else statement to perform certain actions based on whether `soilRead` is greater than \(or less than\) one or more specific values.

#### GATHER TEST VALUES

Depending on the specific purpose of the moisture sensor in your device, you may need to gather some test values under different conditions \(such as dry vs. wet\) to see what the moisture values might actually be where your device will be used. This will help you determine which values to use in your code to make decisions. For example, if the moisture sensor will be used to send notifications when the soil is either too dry or too wet, what values will be used to decide this?

For example, the code below uses a value of `500` to decide whether the soil is too dry and a value of `3500` to decide whether the soil is too wet. However, you would need to gather test data to determine whether these values should be higher or lower.

```cpp
if (soilRead < 500) {
    // send notification when soil is too dry
    Particle.publish("soil", "dry");
}
else if (soilRead > 3500) {
    // send notification when soil is too wet
    Particle.publish("soil", "wet");
}
```

### Map Value to Custom Range {#mapping-dial-position-to-custom-range-of-values}

In many cases, it may not be convenient to work with a value that ranges from 0-4095. Instead, it might be easier to have a value within a smaller custom range \(such as:  0-10, 0-100, etc.\) that makes more sense for your particular task.

The `map()` function can be used to convert a value from its original range \(such as 0-4095\) into a new range of your choice. You decide the minimum and maximum values for the new range.

For example, if the moisture sensor were being used to automatically turn a sprinkler system on and off, you might want the sensor to return a value between 0-100 as an easier way to determine the relative soil moisture.

Add this code \(modify as necessary\) to your app within the `loop()` function or a custom function:

```cpp
digitalWrite(soilPower, HIGH);
delay(10);
int soilRead = analogRead(soil);
digitalWrite(soilPower, LOW);​
int minValue = 0;
int maxValue = 100;
int soilValue = round(map(soilRead, 0, 4095, minValue, maxValue + 1));
// add code to do something with soilValue
```

As necessary, change the values assigned to `minValue` and `maxValue` to whatever numbers you want to use for your custom range. Also, the `minValue` **doesn't** have to be zero.

Be sure to add code to do something with `soilValue`. For example, this might be an if-else statement to perform certain actions based on whether `soilValue` is greater than \(or less than\) one or more specific values.

**NOTE:** The code uses the `round()` method to round the mapped value to the nearest integer because the `map()` method returns a `float` \(decimal value\). Also, inside the `map()` method, the code intentionally adds 1 to the `maxValue` because otherwise it is very difficult to get the maximum value even if the soil moisture is very high.

#### CUSTOM FUNCTION TO READ MOISTURE SENSOR

You could incorporate this code into a custom function called `checkSoil()` that will read the soil moisture sensor and return a value mapped to a custom range:

```cpp
int checkSoil() {
    digitalWrite(soilPower, HIGH);
    delay(10);
    int soilRead = analogRead(soil);
    digitalWrite(soilPower, LOW);​
    int minValue = 0;
    int maxValue = 100;
    int mapValue = round(map(soilRead, 0, 4095, minValue, maxValue + 1));
    return mapValue;
}
```

If necessary, change the variable names for the sensor's pins to match your variable names. You can also change the values assigned to `minValue` and `maxValue` to whatever numbers you want to use for your custom range.

The `checkSoil()` function will return the mapped sensor value as an integer, which your code should store in a variable of data type `int`.

For example, to call the `checkSoil()` function within the `loop()` function:

```cpp
int soilValue = checkSoil();
// add code to do something with soilValue
```

