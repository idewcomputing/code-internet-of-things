# Web App

You can create a web app that interacts with your Photon device through Particle Cloud.

Your web app will consist of an HTML file named`index.html`, a CSS file named `style.css`, and a JavaScript file named `code.js`.

This section contains starter code that you can use for your HTML, CSS, and JS files. You'll need to add to the starter code \(and modify certain parts\).

## HTML

You can use this starter code for your HTML file named `index.html`:

```markup
<!DOCTYPE html>
<html>
    <head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Smart Device</title>
        <link href="style.css" rel="stylesheet" type="text/css">
    </head>
    <body>
        <!-- Add HTML for your web app -->
        
        
        
        <!-- Load JavaScript files -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/particle-api-js/7.3.0/particle.min.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
        <script src="code.js"></script>
    </body>
</html>
```

{% hint style="success" %}
**COPY CODE:** When using this IoT code guidebook, you can copy a code block simply by clicking the **copy icon** displayed in the upper right of the code block.
{% endhint %}

This HTML does three main things:

1. It loads a CSS stylesheet file.
2. It loads three JavaScript files.
3. It has blank lines where you'll add HTML for your specific web app.

#### LOAD CSS STYLESHEET

In the `<head>` section, there is a `<link>` tag to load a CSS stylesheet file named `style.css` that you'll use to modify the appearance of certain HTML elements in your web app.

#### LOAD JAVASCRIPT FILES

At the bottom of the `<body>` section, there are `<script>` tags to load several JavaScript files into your web app:

1. Particle API JS library:  `particle.min.js`
2. jQuery JS library:  `jquery.min.js`
3. Your web app JS file:  `code.js`

The [Particle API JS library](https://docs.particle.io/reference/javascript/) contains methods to allow your web app to interact with your Photon device through Particle Cloud. You'll use Particle methods in your web app JS file.

The [jQuery JS library](https://api.jquery.com/) contains methods that make it easy to modify the content and style of your web app by dynamically changing its HTML and CSS. You'll use jQuery methods in your web app JS file.

#### BLANK LINES FOR YOUR HTML

In the `<body>` section, there are several blank lines are where you will add HTML for your web app.  \(You can use more lines, obviously.\)  This is where you might display text, images, links, buttons, etc.

#### HOW TO CREATE MULTIPLE SCREENS

Your web app should consist of **single HTML page**. If you want different screens for your web app, then create a separate `<div>` section for each screen, and give each `<div>` a unique [id name](https://www.w3schools.com/html/html_id.asp) along with a [class name](https://www.w3schools.com/html/html_classes.asp) shared by all the screen `<div>` sections.

This will allow your web app JS to use [jQuery code to show one screen while hiding the other screens](https://www.w3schools.com/jquery/jquery_hide_show.asp). First, you use jQuery to `hide()` all the screens \(by selecting the class name\), and then use jQuery to `show()` one specific screen \(by selecting its unique id name\). To switch to a different screen, just `hide()` all the screens again, and then `show()` the new screen.

## CSS

You can use this starter code for your CSS file named `style.css`:

```css
/* Add or modify CSS for your web app */
body {
    font-family:  Helvetica, Arial, sans-serif;
    font-size: 1em;
    text-align: center;
}


```

This CSS styles the `<body>` section of your web app. However, you can modify this CSS if desired.

You'll typically want to add CSS to style other HTML elements in your web app, in order to produce the desired layout and appearance for your app's user interface.

## JS

You can use this starter code for your JS file named `code.js` \(be sure to modify\):

```javascript
var particle = new Particle();
var myDevice = "0000"; // Photon device ID
var myToken = "0000"; // Photon access token

// Add JS for your web app


```

{% hint style="danger" %}
**IMPORTANT:**  You **must** modify this JS code to insert your actual Photon device ID and access token. Otherwise, your web app will **not** work properly.
{% endhint %}

This JS creates a new `Particle()` object and assigns it to a global variable named `particle`. This object has built-in methods \(functions\) that can be used to interact with your Photon device through Particle Cloud.

This JS also declares global variables to store your Photon device ID and access token. You must modify these lines to list [your actual device ID and access token](particle-cloud/web-app-prep-steps.md#device-id-and-access-token), which you will need to get from your team's Particle Build account.

Then you'll need to add the other necessary JS for your web app. Because your HTML file loaded the Particle API JS library and jQuery JS library, you can include Particle statements and jQuery statements within your JS code.

Review the reference section on [Particle Cloud](particle-cloud/) to learn how to make your web app JS interact with your Photon device app.

## Resources

If you want to learn more about web development or need a quick reference, consult these tutorials and references from [W3Schools](https://www.w3schools.com/):

* [HTML](https://www.w3schools.com/html/default.asp)
* [CSS](https://www.w3schools.com/css/default.asp)
* [JavaScript](https://www.w3schools.com/js/default.asp)
* [jQuery](https://www.w3schools.com/jquery/default.asp)





