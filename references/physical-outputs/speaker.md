# Speaker

The speaker included in the Photon kit can be used to produce tones or play simple music \(note by note\).

![Speaker](../../.gitbook/assets/speaker.jpg)

## How to Connect Speaker

A speaker is a [polarized](https://learn.sparkfun.com/tutorials/polarity) part, meaning there is one way to correctly connect its positive and negative terminals. If a polarized part is connected incorrectly \(by switching the positive and negative\), the part may not work or could become damaged.

The speaker in your Photon kit has a positive leg and a negative leg. These can be identified by labels on the bottom of the speaker:

![](../../.gitbook/assets/speaker-polarity.jpg)

### Requires PWM Pin

The positive leg of the speaker must be connected to an I/O pin capable of [pulse-width modulation](https://learn.sparkfun.com/tutorials/pulse-width-modulation) \(PWM\), which is a process used to make a digital output signal \(which has only two values: HIGH or LOW\) act like an analog output signal \(which has a range of values\).

These I/O pins on your Photon circuit board are capable of PWM: D0, D1, D2, D3, A4, A5.

### Connect to Breadboard

To connect a speaker to your Photon using the breadboard, you will need:

* Speaker
* 2 jumper wires \(use different colors to help identify them\)

| Speaker | Photon Pin |
| :--- | :--- |
| Positive Leg | any I/O pin capable of PWM |
| Negative Leg | GND |

Here are the steps to connect the speaker to your Photon using the breadboard:

1. Insert the positive and negative legs of the speaker into **different** terminal strip rows on the breadboard. \(Different terminal strip rows have different row numbers.\)
2. Plug one end of a **jumper wire** into the **same** terminal strip row as the **positive** leg of the speaker. Plug the other end of this jumper wire into a **PWM-capable** I/O pin on the Photon circuit board.
3. Plug one end of the **other jumper wire** into the **same** terminal strip row as the **negative** leg of the speaker. Plug the other end of this jumper wire into a pin hole connected to GND:  either plug it into a negative power rail \(which is connected to GND via a different jumper wire\), or plug it directly into a GND pin on the Photon circuit board.

Here's a wiring diagram showing a possible way to connect a speaker:

![](../../.gitbook/assets/experiment-5.jpg)

Keep in mind that your connection can look different than this example diagram:

* Your speaker legs could be inserted into **different row numbers** on the breadboard. \(The example connects the negative leg to row 3 and the positive leg to row 5\).
* Your speaker legs could be inserted into a **different column** on the breadboard. \(The example connects the LED legs into column F of the terminal strip rows\).
* The positive leg of your speaker could connect to a **different I/O pin**. \(The example connects to the D2 pin on the Photon circuit board\).
* The negative leg of your speaker could connect \(through a jumper wire\) to **either a negative power rail or a different GND pin**. \(There are three available GND pins on the Photon circuit board.\)



