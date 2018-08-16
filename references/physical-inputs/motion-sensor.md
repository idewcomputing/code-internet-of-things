# Motion Sensor

The motion sensor included in your Photon kit uses passive infrared \(PIR\) light to detect movement in the surrounding area up to about 10 feet away.

![Motion Sensor](../../.gitbook/assets/motion-sensor.jpg)

## How to Connect Motion Sensor

The motion sensor has a 3-wire JST connector with 3 pins for plugging into a breadboard. \(If the end of your wire connector doesn't have 3 pins, attach the [JST right angle connector](https://www.sparkfun.com/products/9750) included in your kit.\)

To connect a motion sensor to your Photon using the breadboard, you will need:

* Motion sensor \(with 3-pin JST right angle connector\)
* 3 jumper wires \(use different colors to help identify them; it may help to match the sensor wires\)

| Motion Sensor | Photon Pin |
| :--- | :--- |
| Black - Data | any I/O pin |
| White - Ground | GND |
| Red - Power \(5-12V\) | 5V through VIN or V-USB |

Here are the steps to connect the motion sensor to your Photon using the breadboard:

1. Insert the 3 pins of the motion sensor connector into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as the **sensor's black wire**. Plug the other end of this jumper wire into an I/O pin on the Photon circuit board.
3. Plug one end of a **second jumper wire** into the **same** terminal strip row as the **sensor's white wire**. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.
4. Plug one end of a **third jumper wire** into the **same** terminal strip row as the **sensor's red wire**. Plug the other end of this jumper wire into either the VIN pin or V-USB pin on the Photon circuit board. If your Photon is being powered through the barrel jack, use the VIN pin. Otherwise, if your Photon is being powered through the Micro-USB port, use the V-USB pin.

Here's a wiring diagram showing a possible way to connect a motion sensor:

![](../../.gitbook/assets/experiment-9a.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your motion sensor pins could be inserted into different row numbers on either breadboard side. \(The example connects the sensor pins to rows 16-18 on the left side of the breadboard\).
* Your motion sensor pins could be inserted into a different column on the breadboard. \(The example connects the sensor pins into column A of the terminal strip rows\).
* The black wire of your motion sensor could be connected \(through a jumper wire\) to a different I/O pin than the example \(which happens to connect to the D0 pin on the Photon circuit board\).
* The white wire of your motion sensor could be connected \(through a jumper wire\) to either a negative power rail or a different GND pin.
* The red wire of your motion sensor could be connected \(through a jumper wire\) to a different I/O pin than the example \(which happens to connect to the D0 pin on the Photon circuit board\).
* Your negative power rail on the breadboard could connect to a different GND pin than the example  \(there are two other available GND pins on the Photon circuit board\).

