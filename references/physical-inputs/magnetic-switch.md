# Magnetic Switch

Your Photon kit includes a [magnetic switch](https://www.sparkfun.com/products/13247) that can be used to detect whether a door, window, drawer, box, etc. is open or closed.

![Magnetic Switch](../../.gitbook/assets/magnetic-switch.jpg)

The switch consists of two pieces, and it can detect whether or not these two pieces are close to each other. If the two pieces are within 20 mm \(about 0.75 inches\) of each other, the switch detects that is it "closed" – otherwise, the switch will detect that it is "open."

The piece with the wires contains a special switch called a [reed switch](http://www.explainthatstuff.com/howreedswitcheswork.html) that moves in response to the presence \(or absence\) of a magnetic field. The other piece \(without the wires\) contains a small magnet, so it can activate the reed switch when the two pieces are close to each other.

For example, the piece with the wires \(the reed switch\) could be attached on a stationary door frame, and the piece without the wires \(the magnet\) would be attached on the door near its edge. The two pieces would be installed so they are very close together when the door is closed. When the door is opened, the reed switch will detect that the magnet has moved away.

These magnetic switches are commonly used in security systems for doors and windows, but they are also used in many other products. For example, a doorbell uses a magnetic switch. Magnetic switches are also used in many laptops and tablets to detect when its lid or cover is either open or closed, in order to automatically wake up the device or put it to sleep.

## How to Connect Switch



To connect a push button to your Photon using the breadboard, you will need:

* Magnetic Switch
* 2 jumper wires \(use different colors to help identify them\)

| Magnetic Switch | Photon Pin |
| :--- | :--- |
| First Wire \(either one\) | any I/O pin |
| Second Wire | GND |

Here are the steps to connect the magnetic switch to your Photon using the breadboard:

1. Insert the two wires of the magnetic switch into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as **one switch wire**. Plug the other end of this jumper wire into an I/O pin on the Photon circuit board.
3. Plug one end of the **other jumper wire** into the **same** terminal strip row as the **other switch wire**. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail on the breadboard \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a magnetic switch:

![](../../.gitbook/assets/experiment-9b.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your magnetic switch wires could be inserted into **different row numbers** on either breadboard side. \(The example connects the wires to rows 17-18 on the left side of the breadboard.\)
* Your magnetic switch wires could be inserted into a **different column** on the breadboard. \(The example connects the LED legs into column A of the terminal strip rows\)
* Your magnetic switch could connect \(through a jumper wire\) to a **different I/O pin**. \(The example connects to the D0 pin on the Photon circuit board.\)
* Your magnetic switch could connect \(through a jumper wire\) **either to a different GND pin or to a negative power rail connected to a GND pin**. \(There are three available GND pins on the Photon circuit board.\)

## How to Code Switch

explain



