# Ultrasonic Sensor

{% hint style="info" %}
**ADD-ON COMPONENT:**  The SparkFun Photon Kit does **NOT** include an ultrasonic sensor as a standard component. However, SparkFun sells the [HC-SR04 Ultrasonic Sensor](https://www.sparkfun.com/products/13959), which can be easily connected to a Photon. Your teacher may have added this sensor to your kit. 
{% endhint %}

An ultrasonic sensor uses sonar to measure the distance to an object, similar to how bats and dolphins use [echolocation](https://en.wikipedia.org/wiki/Animal_echolocation) for navigation and hunting.

![Ultrasonic Sensor \(HC-SR04\)](../../.gitbook/assets/ultrasonic-sensor.jpg)

An ultrasonic sensor has a speaker that can transmit high-frequency sound \(beyond the range of human hearing\). The sensor also has a matching receiver \(i.e., microphone\) that detects the echo of the high-frequency sound when it reflects back from an object. By measuring how much time it takes for the echo to arrive, you can calculate the distance between the sensor and the object.

The HC-SR04 ultrasonic sensor measures distances in a narrow cone of about 15° directly in front of the sensor. This sensor can detect obstacles located up to 400 cm away \(about 13 feet\). The sensor measurements are very accurate, within about 3 mm \(about 0.1 inch\) of the actual distance.

## How to Connect Ultrasonic

The HC-SR04 ultrasonic sensor has 4 pins for plugging into a breadboard. Each pin is labeled on the sensor's circuit board.

To connect the ultrasonic sensor to your Photon using the breadboard, you will need:

* Ultrasonic Sensor \(HC-SR04\)
* 4 jumper wires \(use different colors to help identify them\)

| Ultrasonic Sensor | Photon Pin |
| :--- | :--- |
| VCC | 5V through VIN or V-USB |
| Trig | any I/O pin |
| Echo | any I/O pin |
| GND | GND |

{% hint style="success" %}
**5V REQUIRED:** The ultrasonic sensor requires 5V of power to operate.

* If your Photon is being powered through the **barrel jack**, connect to the **VIN** pin.
* If your Photon is being powered through the **Micro-USB** port, connect to the **V-USB** pin.
{% endhint %}

Here are the steps to connect the ultrasonic sensor to your Photon using the breadboard:

1. Insert the 4 pins of the ultrasonic sensor into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\) It is recommended to insert the sensor on the left half of the breadboard with the transmitter and receiver **facing away from the Photon**.
2. Plug one end of a **jumper wire** into the **same** terminal strip row as the **sensor's VCC pin**. Plug the other end of this jumper wire into either the VIN pin or V-USB pin on the Photon circuit board \(or to a **positive** power rail on the breadboard that is connected to VIN or V-USB\). If your Photon is being powered through the barrel jack, connect to the VIN pin. Otherwise, if your Photon is being powered through the Micro-USB port, connect to the V-USB pin.
3. Plug one end of a **second jumper wire** into the **same** terminal strip row as the **sensor's Trig pin**. Plug the other end of this jumper wire into an I/O pin on the Photon circuit board.
4. Plug one end of a **third jumper wire** into the **same** terminal strip row as the **sensor's Echo pin**. Plug the other end of this jumper wire into an I/O pin on the Photon circuit board.
5. Plug one end of a **fourth jumper wire** into the **same** terminal strip row as the **sensor's GND pin**. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect the ultrasonic sensor:

![](../../.gitbook/assets/ultrasonic-wiring.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your ultrasonic sensor pins could be inserted into **different row numbers**. \(The example connects the sensor pins to rows 23-26 on the left side of the breadboard.\)
* Your motion sensor pins could be inserted into a **different column** of the breadboard. \(The example connects the sensor pins into column B of the terminal strip rows.\)
* Your sensor's VCC pin could connect \(through a jumper wire\) to **either the VIN pin or V-USB pin \(or to a positive power rail that's connected to one of these pins\).** \(The example connects directly to the VIN pin.\)
* Your sensor's Trig pin could connect \(through a jumper wire\) to a **different I/O pin**. \(The example connects to the D2 pin.\)
* Your sensor's Echo pin could connect \(through a jumper wire\) to a **different I/O pin**. \(The example connects to the D3 pin.\)
* Your sensor's GND pin could connect \(through a jumper wire\) to **either to a GND pin or to a negative power rail connected to a GND pin**. \(There are three available GND pins.\)

## How to Code Ultrasonic

explain



  




