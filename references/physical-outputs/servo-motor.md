# Servo Motor

The servo motor included in your Photon kit can rotate back or forth to any position between 0° and ~180° and hold its position.

![Servo Motor and Horns](../../.gitbook/assets/servo-motor-plus-mounts.jpg)

The servo motor comes with 4 different plastic mounts called "horns" that can be attached to the motor axis \(the white part sticking out of the top of the motor – this is what actually rotates\). There is a single-arm horn, a double-arm horn, a four-point horn, and a circular horn. Each horn slips onto the motor axis \(the horn and axis have matching "teeth"\). Each horn has holes, which can allow you to attach something to the horn using the included screws.

![](../../.gitbook/assets/servo-type-compare.png)

This servo motor is designed to rotate to a specific angle and hold its position. It does **NOT** rotate continuously, like a motor used in a fan or an engine. If your IoT device requires a motor that can rotate continuously, then you need a [gear motor](https://www.sparkfun.com/products/11696) or a [continuous rotation servo motor](https://www.sparkfun.com/products/9347).

## How to Connect Servo Motor

The servo motor has a built-in 3-wire connector: just plug 3 jumper wires into the connector and then plug the other end of the jumper wires into a breadboard or directly to the Photon. To make it easier to remember which wire is which, use corresponding white, red, and black jumper wires to match the servo motor wires.

### Requires PWM Pin {#requires-pwm-pin}

The white wire of the servo motor must be connected to an I/O pin capable of [pulse-width modulation](https://learn.sparkfun.com/tutorials/pulse-width-modulation) \(PWM\), which is a process used to make a digital output signal \(which has only two values: HIGH or LOW\) act like an analog output signal \(which has a range of values\).

These I/O pins on your Photon circuit board are capable of PWM output: A4, A5, D0, D1, D2, D3.

### Connect to Photon

To connect a motion sensor to your Photon using the breadboard, you will need:

* Servo Motor \(with 3-wire connector\)
* 3 jumper wires \(use different colors to help identify them; it may help to match the motor wires\)

| Servo Motor | Photon Pin |
| :--- | :--- |
| White - Data | any I/O pin capable of PWM output |
| Red - Power \(4.8-6V\) | 5V through VIN or V-USB |
| Black - Ground | GND |

Here are the steps to connect the servo motor to your Photon using the breadboard:

1. Plug one end of a **jumper wire** into the **motor's white wire connector**. Plug the other end of this jumper wire into a **PWM-capable** I/O pin on the Photon circuit board.
2. Plug one end of a **second jumper wire** into the **motor's red wire connector**. Plug the other end of this jumper wire into either the VIN pin or V-USB pin on the Photon circuit board \(or to a **positive** power rail on the breadboard that is connected to VIN or V-USB\). If your Photon is being powered through the barrel jack, connect to the VIN pin. Otherwise, if your Photon is being powered through the Micro-USB port, connect to the V-USB pin.
3. Plug one end of a **third jumper wire** into the **motor's black wire connector**. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a servo motor \(ignore the wiring for the push button\):

![](../../.gitbook/assets/experiment-7.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your servo motor's white wire could connect to a **different I/O pin capable of PWM output**. \(The example connects to the D0 pin on the Photon circuit board\).
* Your servo motor's red wire could connect \(through a jumper wire\) to **either the VIN pin or V-USB pin \(or to a positive power rail that's connected to one of these pins\).** \(The example connects directly to the V-USB pin on the Photon circuit board\).
* Your servo motor's black wire could connect \(through a jumper wire\) to **either a negative power rail or a different GND pin**. \(There are three available GND pins on the Photon circuit board.\)

### Connect Horn to Motor

Be sure to attach one of the horns to your servo motor. Otherwise, it won't provide much use to your device.

Later, once you test out your code to rotate the servo motor, you may need to remove and re-position the horn, so it's lined up where you want it to be. The easiest way to do this is to rotate the servo motor to 0° and then re-position the horn to be pointed correctly for this particular angle.

## How to Code Servo Motor

explain

