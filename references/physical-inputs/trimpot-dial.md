# Trimpot Dial

Your Photon kit includes a "trimpot" \(trimmable potentiometer\) that can be rotated and used as a dial. A potentiometer is a variable resistor that can be adjusted by sliding, rotating, or another type of physical interaction. Potentiometers are used in various devices such as: joysticks and game controllers, control knobs and sliders, dimmer switches for lights, volume knobs for stereos, etc.

![Trimpot Dial \(side view\)](../../.gitbook/assets/trimpot.jpg)

The trimpot dial can be rotated clockwise or counterclockwise approximately 270° \(it does **NOT** rotate all the way around\). The position of the dial can be measured and used as an input for a value that has a range from minimum to maximum.

![Trimpot \(top view\): Max. Range of Rotation](../../.gitbook/assets/trimpot-max.jpg)

## How to Connect Trimpot

To connect a trimpot dial to your Photon using the breadboard, you will need:

* Trimpot
* 3 jumper wires \(use different colors to help identify them\)

| Trimpot | Photon Pin |
| :--- | :--- |
| Outer Leg \(either one\) | 3.3V |
| Middle Leg | any analog I/O pin \(A0, A1, A2, A3, A4, or A5\) |
| Outer Leg \(other one\) | GND |

{% hint style="success" %}
**3.3V MAXIMUM:**  Analog inputs, such as the trimpot, require 3.3V of power for accurate measurements. Connect the trimpot to the 3.3V pin on your Photon, or connect it to a positive power rail on the breadboard that's connected to the 3.3V pin.
{% endhint %}

Here are the steps to connect the trimpot to your Photon using the breadboard:

1. Insert the three metal legs of the trimpot into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as an **outer leg** of the trimpot \(either outer leg\). Plug the other end of this jumper wire into the 3.3V pin on the Photon circuit board \(or plug it into a positive power rail on the breadboard that's connected to the 3.3V pin via a different jumper wire\).
3. Plug one end of a **second jumper wire** into the same terminal strip row as the **middle leg** of the trimpot. Plug the other end of this jumper wire into any analog I/O pin on the Photon circuit board. 
4. Plug one end of the **third jumper wire** into the **same** terminal strip row as the **other outer leg** of the trimpot. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail on the breadboard \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a trimpot \(ignore the wiring for the three push buttons\):

![](../../.gitbook/assets/experiment-4.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your trimpot legs could be inserted into **different row numbers** on either breadboard side. \(The example connects the trimpot legs to rows 26-28 on the right side of the breadboard\).
* Your trimpot legs could be inserted into a **different column** of the breadboard. \(The example connects the trimpot legs into column F of the terminal strip rows\).
* Your trimpot could connect \(through a jumper wire\) to a different analog I/O pin on the Photon circuit board. \(The example connects the trimpot to the A0 pin.\)
* Your trimpot could connect \(through a jumper wire\) **either directly to the 3.3V pin** **or to a positive power rail on the breadboard that's connected to the 3.3V pin.**
* Your trimpot could connect \(through a jumper wire\) **either directly to a GND pin or to a negative power rail that's connect to a GND pin**. \(There are three available GND pins on the Photon circuit board.\)

## How to Code Trimpot

explain

