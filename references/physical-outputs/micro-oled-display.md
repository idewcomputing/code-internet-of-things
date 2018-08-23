# Micro OLED Display

The Micro OLED display included in your Photon kit is a monochrome, blue-on-black screen that is 64 pixels in width and 48 pixels in height. It can be used to display text, simple graphics, or a combination.

![Micro OLED Display](../../.gitbook/assets/micro-oled.jpg)

## How to Connect Micro OLED

To connect the Micro OLED display to your Photon using the breadboard, you will need:

* Micro OLED display
* 7 jumper wires \(use different colors to help identify them\)

The Micro OLED has pins located along the top edge of the display. There are labels for each pin printed on the underside of the Micro OLED circuit board.

If the pins along the top edge of the display were numbered left to right as 1-8, the connections for the jumper wires will be:

| OLED Pin | Photon Pin |
| :--- | :--- |
| Pin 1 – CS | A2 |
| Pin 2 – RST | D6 |
| Pin 3 – D/C | D5 |
| Pin 4 – SDO | \(None\) |
| Pin 5 – SCK | A3 |
| Pin 6 – SDI | A5 |
| Pin 7 – 3V3 | 3.3V |
| Pin 8 – GND | GND |

Here are the steps to connect the Micro OLED to your Photon using the breadboard:

1. Insert the 8 pins of the Micro OLED into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as the **first OLED pin \(CS\)**. Plug the other end of this jumper wire into its corresponding pin on the Photon circuit board.
3. Repeat step 2 with the other jumper wires until each OLED pin is connected to its correct Photon pin. **NOTE:** The **fourth OLED pin \(SDO\)** will **not** be connected to anything.

{% hint style="warning" %}
**TWIN PINS:** Analog pins A2, A3, A4, and A5 are each represented by **two** pins on the Photon board. The duplicate pins are labeled as: SS/A2, SCK/A3, MISO/A4, MOSI/A5.

However, the Micro OLED has to connect to **only one** A2 pin – **not** both. The same goes for connecting the Micro OLED to the A3 and A5 pins.

The only limitation is that once you connect the Micro OLED, you will **not** be able to have a different part \(such as an LED, etc.\) connected to the other A2, A3, or A5 pins.
{% endhint %}

Here's a wiring diagram showing a possible way to connect a servo motor \(ignore the wiring for the three push buttons\):

![](../../.gitbook/assets/experiment-11.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your Micro OLED could connect \(through jumper wires\) to the **other A2, A3, and A5 pins** located on the lower left side of the Photon circuit board.
* Your Micro OLED 3V3 pin could connect \(through a jumper wire\) **either directly to the 3.3V pin** **or to a positive power rail that's connected to the 3.3V pin.**
* Your Micro OLED GND pin could connect \(through a jumper wire\) to **either directly to a GND pin or to a negative power rail that's connect to a GND pin**. \(There are three available GND pins on the Photon circuit board.\)

## How to Code Micro OLED

The basic steps to control the Micro OLED display in your app code are:

1. Include the SparkFun Micro OLED library in your app.
2. Define the I/O pin numbers for certain Micro OLED pins.
3. Create a `MicroOLED` object assigned to a global variable called `oled`.
4. Use the `oled.begin()` method to start the display in the `setup()` function.
5. Use various `oled` methods to display text or simple graphics on the screen.

### Include Library

Your Photon app must include a code library that will allow you to control the Micro OLED display.

![Libraries Icon](../../.gitbook/assets/pb-library-icon.png)

1. In Particle Build, click on the Libraries icon to open the Libraries menu panel.
2. Type `oled` into the search field. Select the result called: **SPARKFUNMICROOLED**
3. Click the button to "Include in Project"
4. Select the name of your Photon app, and then click the "Confirm" button

Particle Build will **automatically** insert this `#include` statement at the beginning of your app code:

```cpp
// This #include statement was automatically added by the Particle IDE.
#include <SparkFunMicroOLED.h>
```

### Define Pins & Create Object

You need to define the I/O pin numbers for certain Micro OLED pins. This is similar to declaring global variables \(except defined values are not allowed to change\).

You will also need to create an object using the `MicroOLED` class defined in the included library, and assign this object to a global variable.

Add this code **before** the `setup()` function:

```cpp
#define PIN_OLED_RST D6
#define PIN_OLED_DC  D5
#define PIN_OLED_CS  A2
MicroOLED oled(MODE_SPI, PIN_OLED_RST, PIN_OLED_DC, PIN_OLED_CS);
```

The **first three lines of code** define the I/O pin numbers for three specific OLED pins.

The **fourth line of code** creates a new object using the `MicroOLED` class, and assigns the object to a global variable named `oled`. Several parameters are included when creating the object.

### Start OLED in Setup

The `oled.begin()` method is used to start the Micro OLED display, which should typically be done when your app first starts running.

Add this code statement within the `setup()` function to start the OLED display:

```cpp
oled.begin();
```

### Display Text

Displaying text on the Micro OLED screen requires a sequence of five steps:

1. Clear the screen using the `oled.clear()` method.
2. Set the cursor position using the `oled.setCursor()` method.
3. Select the font size using the `oled.setFontType()` method.
4. Print text \(or variable values\) using the `oled.print()` or `oled.println()` methods.
5. Display the text using the `oled.display()` method.



