# Magnetic Switch

Your Photon kit includes a [magnetic switch](https://www.sparkfun.com/products/13247) that can be used to detect whether a door, window, drawer, box, etc. is open or closed.

![Magnetic Switch](../../.gitbook/assets/magnetic-switch.jpg)

The switch consists of two pieces, and it can detect whether these two pieces are close to each other:

1. The piece with the wires contains a [**reed switch**](http://www.explainthatstuff.com/howreedswitcheswork.html) that moves in response to the presence or absence of a magnetic field.
2. The other piece without the wires contains a **magnet**, so it can activate the reed switch when the two pieces are close to each other.

If the two pieces of the magnetic switch are within 20 mm \(0.75 inches\) of each other, the switch detects that it's "closed" – otherwise, the switch will detect that it's "open."

These magnetic switches are commonly used in security systems for doors and windows, but they are also used in many other products. For example, a doorbell uses a magnetic switch to detect when it is being pressed. Magnetic switches are also used in many laptops and tablets to detect when the lid/cover is open or closed, in order to automatically wake up the device or put it to sleep.

## How to Connect Switch

The reed switch \(the piece with the wires\) will be connected to the Photon. Then the reed switch will be attached to a **stationary** edge near something that opens \(such as:  door, window, drawer, etc.\). For example, the reed switch could be attached to the edge of a door frame – but **not** to the door itself.

The magnet \(the piece **without** wires\) would be attached to the object \(door, window, etc.\) that actually moves when opened. The two pieces of the magnetic switch should be positioned so they are very close together \(no more than 0.75 inches apart\) when the object \(door, window, etc.\) is closed.

![Installing Magnetic Switch on Door](../../.gitbook/assets/magnetic-switch-install.jpg)

To connect a magnetic switch to your Photon using the breadboard, you will need:

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

* Your magnetic switch wires could be inserted into **different row numbers** on either breadboard side. \(The example connects the switch wires to rows 17-18 on the left side of the breadboard.\)
* Your magnetic switch wires could be inserted into a **different column** on the breadboard. \(The example connects the switch wires into column A of the terminal strip rows.\)
* Your magnetic switch could connect \(through a jumper wire\) to a **different I/O pin**. \(The example connects to the D0 pin on the Photon circuit board.\)
* Your magnetic switch could connect \(through a jumper wire\) **either to a different GND pin or to a negative power rail connected to a GND pin**. \(There are three available GND pins on the Photon circuit board.\)

## How to Code Switch

explain



