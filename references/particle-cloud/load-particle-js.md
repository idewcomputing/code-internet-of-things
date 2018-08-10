# Load Particle JS

## Load JS Files

### particle.min.js

Load Particle API JS library in HTML file using `<script>` tag:

```markup
<script src="https://cdn.jsdelivr.net/npm/particle-api-js@7.2.3/lib/Particle.min.js"></script>
```

Alternatively, you can download a copy of the Particle API JS file, and place the file into the same folder as your HTML file. In this case, your `<script>` tag would load the file directly from the folder:

```javascript
<script src="particle.min.js"></script>
```

### code.js

After loading the Particle API JS file \(using one of the methods describe above\), your web app also needs to load a JavaScript file containing your own code to interact with your Photon device. This will be loaded using another `<script>` tag.

Then load your JavaScript file in HTML file using `<script>` tag:

```markup
<script src="code.js"></script>
```

{% hint style="success" %}
**IMPORTANT:**  The `<script>` tag in your HTML that loads the Particle API JS file must be listed **before** the `<script>` tag that loads your web app's JavaScript file \(`code.js`\). Otherwise, if their order is reversed, your web app won't be able to interact with your Photon.
{% endhint %}

## Create Particle Object

The Particle API JS library defines a class called `Particle()` that can be used to create an object variable with built-in methods \(functions\) to interact with a Photon device through Particle Cloud.

Your web app's JavaScript code must create a new `Particle()` object, and assign it to a global variable, which is typically just named `particle`.

Add this code statement at the beginning of your web app JS code:

```javascript
var particle = new Particle();
```

## Device ID & Access Token

Add global variables for device ID and access token \(get values from your Particle Build account\)

```javascript
var myDevice = "000000000000000000000000"; // Photon device ID
var myToken = "000000000000000000000000"; // Photon access token
```



