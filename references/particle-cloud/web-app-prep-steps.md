# Web App Prep Steps

In order for your web app to interact with your Photon device through Particle Cloud, you'll need to complete the following preparation steps:

1. Your web app HTML file needs to load several JS files \(such as:  Particle API JS library, etc.\).
2. Your web app JS file needs to create a new `Particle()` object.
3. Your web app JS file needs to declare variables to store your Photon device ID and access token.

Once these steps have been completed, you'll be ready to add code in your web app JS to read device variables, call device functions, and get device event notifications.

## Load JS Files

Your web app HTML file \(`index.html`\) should include `<script>` tags to load these JavaScript files:

1. Particle API JS library:  `particle.min.js`
2. jQuery JS library:  `jquery.min.js`
3. Your web app JS file:  `script.js`

The [Particle API JS library](https://docs.particle.io/reference/javascript/) contains methods to allow your web app to interact with your Photon device through Particle Cloud. You'll use Particle methods in your web app JS file.

The [jQuery JS library](https://api.jquery.com/) contains methods that make it easy to modify the content and style of your web app by dynamically changing its HTML and CSS. You'll use jQuery methods in your web app JS file.

{% hint style="info" %}
**JQUERY = OPTIONAL:**  Loading jQuery is optional. However, it will be much easier to code your web app JS if you can incorporate jQuery statements.
{% endhint %}

{% hint style="success" %}
**IMPORTANT:**  The `<script>` tag in your HTML that loads the Particle API JS file \(`particle.min.js`\) must be listed **before** the `<script>` tag that loads your web app JS file \(`script.js`\). Otherwise, if their order is reversed, your web app won't be able to interact with your Photon.
{% endhint %}

### Option 1: Load from CDN

If possible, use a content delivery network \(such as [cdnjs](https://cdnjs.com/) or [jsDelivr](https://www.jsdelivr.com/)\) to load the Particle API JS library and jQuery JS library.

Your web app JS file will be loaded as a local file from your web app folder \(where your HTML and CSS files are located\).

Add this to your web app HTML file **within** the `<body>` section \(just before the closing `</body>` tag\):

```markup
<script src="https://cdnjs.cloudflare.com/ajax/libs/particle-api-js/7.3.0/particle.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script src="script.js"></script>
```

### Option 2: Load Local Files

Alternatively, you could download local copies of the Particle API JS library and jQuery JS library. You will want the **minified** version of each file \(`min.js`\), which has a smaller file size. If necessary, consult with your teacher to be sure you obtain the correct files.

Place the copies of the files into your web app folder \(where your HTML and CSS files are located\).

Add this to your web app HTML file **within** the `<body>` section \(just before the closing `</body>` tag\):

```markup
<script src="particle.min.js"></script>
<script src="jquery.min.js"></script>
<script src="script.js"></script>
```

Be sure the file names listed in the `<script>` tags match the file names in your web app folder.

## Create Web App JS File

Be sure your web app folder contains a JavaScript file named:  `script.js`

This web app JS file will contain your JavaScript code to interact with your Photon device through Particle Cloud. Your JS code will also dynamically modify your HTML and CSS to display updated information from your Photon device.

## Create Particle Object

The Particle API JS library defines a class called `Particle()` that can be used to create an object variable with built-in methods \(functions\) to interact with a Photon device through Particle Cloud.

Your web app JS code must create a new `Particle()` object, and assign it to a global variable, which is typically just named `particle`.

Add this code statement at the beginning of your web app JS code:

```javascript
var particle = new Particle();
```

## Device ID & Access Token

In order for a web app to interact with a Photon device through Particle Cloud, the web app must provide a correct device ID and access token with each request. This ensures your web app communicates with the correct device – and prevents unauthorized apps from communicating with your device.

Your web app JS code will declare global variables to store your Photon device ID and access token. You'll get their values from your Particle Build account.

Add this code towards the beginning of your web app JS code, and then modify it:

```javascript
var myDevice = "0000"; // Photon device ID
var myToken = "0000"; // Photon access token
```

{% hint style="danger" %}
**IMPORTANT:**  You must modify this JS code to insert your actual Photon device ID and access token. Otherwise, your web app will **not** work properly.
{% endhint %}

Your Photon's unique **device ID** is listed in the **Devices** menu of your Particle Build account:

1. Click the **Devices** icon in the left navigation bar.
2. In the **Devices** menu panel, click the drop-down arrow to the right of your Photon device name.
3. Select and copy the device ID.
4. Paste the device ID into your JS code as the value for `myDevice` \(the device ID must be listed within quotation marks\).

Your Photon's unique **access token** is listed in the **Settings** menu of your Particle Build account:

1. Click the **Settings** icon in the left navigation bar.
2. In the **Settings** menu panel, select and copy the access token.
3. Paste the access token into your JS code as the value for `myToken` \(the access token must be listed within quotation marks\).

{% hint style="info" %}
**RESET TOKEN:**  If desired, you can reset your access token in the Settings menu of Particle Build. This generates a new random access token. However, your existing web apps will need to be updated with the new access token, in order to connect to Particle Cloud.
{% endhint %}

