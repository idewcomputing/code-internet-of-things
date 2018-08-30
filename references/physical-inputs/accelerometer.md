# Accelerometer

The triple-axis accelerometer included in your Photon kit can be used to detect changes in motion or orientation in 3 dimensions \(x, y, z\).

![Accelerometer](../../.gitbook/assets/accelerometer.jpg)

Smartphones and tablets use accelerometers to sense the orientation of the device, in order to change the screen orientation to match. Fitness trackers use accelerometers to count steps and measure other activity. In fact, your accelerometer has built-in functions to detect portrait vs. landscape orientation \(useful for device screens\), as well as taps \(useful for activity trackers\).

#### CHANGE IN MOTION {#change-in-motion}

Like the name implies, an accelerometer works by detecting acceleration – a change in motion. If a device with an accelerometer experiences a change in motion \(i.e., speeding up, slowing down, or changing direction\), the accelerometer can sense this change and measure the amount of acceleration in each of the 3 dimensions \(x, y, z\).

#### ORIENTATION \(TILT\) {#orientation-tilt}

Even if a device with an accelerometer is **not** moving, the accelerometer can detect the orientation \(tilt\) of the device by measuring the acceleration due to Earth's gravity, which is a constant downward force acting on all objects. The accelerometer can determine if the object is parallel to the Earth's surface or if it is tilted – and can measure the amount of tilt for each of the 3 dimension \(x, y, z\).

## How to Connect Accelerometer

explain

| Accelerometer | Photon Pin |
| :--- | :--- |
| 3.3V | 3.3V |
| SDA | D0 \(SDA\) |
| SCL | D1 \(SCL\) |
| I2 | \(none\) |
| I1 | \(none\) |
| GND | GND |

The accelerometer has 6 pins, but only 4 of them need to be connected.

explain

![](../../.gitbook/assets/experiment-8.jpg)

## How to Code Accelerometer

The basic steps to control the accelerometer in your app code are:

1. Include the SparkFun MMA8452Q library and Math library in your app.
2. Create a `MMA8452Q` object assigned to a global variable called `accel`.
3. Use the `accel.begin()` method to start the accelerometer in the `setup()` function. If app will detect taps, use the `accel.setupTap()` method to initialize the tap settings.
4. Use custom functions to detect taps or calculate tilt angles using the accelerometer.

### Include Libraries

Your Photon app must include a code library that will allow you to control the accelerometer \(which is an MMA8452Q accelerometer\). You'll also add a Math library that will be used to calculate tilt angles.

![Libraries Icon](../../.gitbook/assets/pb-library-icon.png)

1. In Particle Build, click on the Libraries icon to open the Libraries menu panel.
2. Type `mma8452q` into the search field. Select the result called:  **SparkFunMMA8452Q**
3. Click the button to "Include in Project"
4. Select the title of your Photon app, and then click the "Confirm" button

Particle Build will **automatically** insert this `#include` statement at the beginning of your app code:

```cpp
// This #include statement was automatically added by the Particle IDE.
#include <SparkFunMMA8452Q.h>
```

In addition, you will include a Math library that has additional mathematical functions and constants, which will be needed to calculate tilt angles. \(The Math library is available in Particle Build, but it won't show up in a search of the community libraries.\)

You need to **manually** add this `#include` statement \(after the other `#include` statement\):

```cpp
#include <math.h>
```

### Global Variable {#global-variable}

You need to create a new object using the `MMA8452Q` class in the included SparkFun MMA8452Q library, and assign this object to a global variable named `accel`.

Add this code statement **before** the `setup()` function:

```cpp
MMA8452Q accel;
```

### Start Accelerometer in Setup

The `accel.begin()` method is used to start the accelerometer, which will initialize its settings. \(You do **not** need to set any pin modes for the accelerometer.\)

Add this code statement within the `setup()` function to start the accelerometer:

```cpp
accel.begin(SCALE_2G, ODR_50);
```

The `accel.begin()` method can accept two parameters inside its parentheses \(in this order\):

1. **The scale range**, which determines the range and precision of the acceleration detection. The options for the scale are: `SCALE_2G`, `SCALE_4G`, or `SCALE_8G`. A higher scale can detect larger changes in acceleration but is less precise. A lower scale is more precise. For your app, using `SCALE_2G` is the probably the best choice because it will be the most precise.
2. **The output data range \(ODR\)**, which determines how frequently it outputs new measurements. The ODR is set in Hz \(number of times per second\). The options for the ODR are: `ODR_1`, `ODR_6`, `ODR_12`, `ODR_50`, `ODR_100`, `ODR_200`, `ODR_400`, or `ODR_800`. A higher ODR is faster \(more frequent\), while a lower ODR is slower \(less frequent\). If your device is being powered by a battery, a lower ODR is more energy-efficient. For your app, using `ODR_50` is probably a good choice.

Alternatively, you can exclude the parameters from the `accel.begin()` statement. If you do this, the accelerometer will default to using `SCALE_2G` and `ODR_800`.

#### SETUP FOR TAP DETECTION

If your app will use the accelerometer to detect taps, then use the `accel.setupTap()` method to initialize the settings for tap detection.

If detecting taps, add this code within the `setup()` function \(**after** the `accel.begin()` statement\):

```cpp
    // set up tap detection
    byte threshold = 1; // 2 * 0.063g = 0.063g
    byte pulseTimeLimit = 255; // 0.625 * 255 = 159ms (max)
    byte pulseLatency = 64; // 1.25 * 64 = 640ms
    accel.setupTap(threshold, threshold, threshold, pulseTimeLimit, pulseLatency);
```



