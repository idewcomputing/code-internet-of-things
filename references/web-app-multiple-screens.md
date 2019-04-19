# Web App - Multiple Screens

You can also create a multi-screen web app that interacts with your Photon device through Particle Cloud. Your multi-screen web app will consist of an HTML file named`index.html`, a CSS file named `style.css`, and a JavaScript file named `script.js`.

Your web app will be a [single-page application](https://en.wikipedia.org/wiki/Single-page_application) that dynamically shows different "screens."  Your web app will only have one HTML page, but different `<div>` sections in the HTML will represent different screens. Your web app will only display one specific `<div>` screen at a time, while hiding the other `<div>` screens.

This section contains starter code that you can use for your HTML, CSS, and JS files. You'll need to add to the starter code \(and modify certain parts\).

This starter code has been designed to mimic the appearance and interaction of a native mobile app. A persistent navigation menu with icons will be displayed at the bottom of the  viewport to allow the user to switch between screens to perform different tasks or view different information.

By default, this app code is designed to show 4 different screens \(but you can modify the code to change the number of screens\). This app code also has a `<div>` section that can be use to display an incoming notification from your smart device.

## HTML

You can use this starter code for your HTML file named `index.html`:

```markup
<!DOCTYPE html>
<html>
  <head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title>Smart Device Web App</title>
	<!-- Load Font Awesome for Icons -->
	<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
	<!-- Load CSS stylesheet -->
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <div id="notification">
	  <span class="closebtn" onclick="this.parentElement.style.display='none';">&times;</span>
	  <!-- HTML for Notification -->
	  <p>Notification Message</p>
			
	</div>
	<div class="screen" id="screen1">
	  <!-- HTML for Screen 1 -->
	  <h1>Screen 1</h1>

	</div>
	<div class="screen" id="screen2">
	  <!-- HTML for Screen 2 -->
	  <h1>Screen 2</h1>

	</div> 
	<div class="screen" id="screen3">
	  <!-- HTML for Screen 3 -->
	  <h1>Screen 3</h1>

	</div>
	<div class="screen" id="screen4">
	  <!-- HTML for Screen 4 -->
	  <h1>Screen 4</h1>
	
	</div>
	<div id="navigation">
	  <nav>
		<!-- Menu icons from Font Awesome -->
		<!-- Search for icons at: https://fontawesome.com/icons?d=gallery&m=free -->
		<a class="menu active" onclick="showScreen1()"><i class="fas fa-home fa-2x"></i><br>Screen 1</a>
		<a class="menu" onclick="showScreen2()"><i class="fas fa-user fa-2x"></i><br>Screen 2</a>
		<a class="menu" onclick="showScreen3()"><i class="fas fa-cog fa-2x"></i><br>Screen 3</a>
		<a class="menu" onclick="showScreen4()"><i class="fas fa-bars fa-2x"></i><br>Screen 4</a>			
	  </nav>
	</div>
	<!-- Load JavaScript files -->
	<script src="https://cdnjs.cloudflare.com/ajax/libs/particle-api-js/7.3.0/particle.min.js"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
	<script src="script.js"></script>
  </body>
</html>
```

{% hint style="success" %}
**COPY CODE:** When using this IoT code guidebook, you can copy a code block simply by clicking the **copy icon** displayed in the upper right of the code block.
{% endhint %}

This HTML has been set up to display 4 different screens. However, you can modify the HTML to display more screens \(or fewer screens\).

This HTML does several things:

1. It loads two CSS stylesheet files.
2. It has `<div>` sections to display a notification message and 4 different screens.
3. It has a `<nav>` section to show the icon-based navigation menu for the screens.
4. It loads three JavaScript files.

#### LOAD CSS STYLESHEETs

In the `<head>` section, there is a `<link>` tag to load a CSS stylesheet file named `style.css` that you'll use to modify the appearance of certain HTML elements in your web app.

There is also a `<link>` tag to load a CSS stylesheet from [Font Awesome](https://fontawesome.com/icons?d=gallery&m=free). This will allow you to display different icons using HTML code that you'll copy from Font Awesome.

#### DIV FOR NOTIFICATION

At the beginning of the `<body>` section, there is a `<div>` section with an id name of`"notification"` that can be used to display a popup notification message. This &lt;div&gt; will normally be hidden, but you can use JavaScript to display the notification.

If your web app **won't** need to display notifications, you can delete this `<div>` section \(though you can just leave it and simply not use it - in case, you change your mind later\).

For example, when an event notification is received from your smart device, your JavaScript can make the notification `<div>` appear \(and, if necessary, can customize the message within the notification\). The notification will appear as a popup at the top of the current screen \(though you can change the position if desired\).

#### DIV FOR EACH SCREEN

In the middle of the `<body>` section, there are several `<div>` sections to represent the different screens in your web app.  Each `<div>` section has the same class name of `screen` to classify it as a screen but also has a unique id name to identify it as a specific screen:  `screen1`, `screen2`, `screen3`, or `screen4`.

The starter code within each `<div>` simply displays a heading for the name of the screen \(so you can see that clicking the navigation menu actually does switch screens\).  You'll remove \(or revise\) this heading, and add your own HTML for each screen to display text, images, buttons, etc.

#### NAV FOR SCREEN MENU

Towards the end of the `<body>` section, there is a `<nav>` section to display a navigation menu for switching between the different screens.

The `<nav>` contains anchor tags \(`<a>`\) for each screen. Normally, an anchor tag contains a link to a different HTML page, but in this case, the tags simply have an `onclick` attribute that will call a custom function in your JavaScript that will display a specific `<div>` screen.

Each anchor tag displays an icon from [Font Awesome](https://fontawesome.com/icons?d=gallery&m=free) \(using special `<i>` code\), along with a text label. You can change the icon and the text label.

#### LOAD JAVASCRIPT FILES

At the end of the `<body>` section, there are `<script>` tags to load several JavaScript files into your web app:

1. Particle API JS library:  `particle.min.js`
2. jQuery JS library:  `jquery.min.js`
3. Your web app JS file:  `script.js`

The [Particle API JS library](https://docs.particle.io/reference/javascript/) contains methods to allow your web app to interact with your Photon device through Particle Cloud. You'll use Particle methods in your web app JS file.

The [jQuery JS library](https://api.jquery.com/) contains methods that make it easy to modify the content and style of your web app by dynamically changing its HTML and CSS. You'll use jQuery methods in your web app JS file.

## CSS

You can use this starter code for your CSS file named `style.css`:

```css
/* Add or modify CSS for your web app */

* {
  box-sizing: border-box; /* use traditional box model sizing */
}

body {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 1em;
  margin: 0;
  padding: 0;
  text-align: center;
}

/* #notification  */
#notification {
  display: none; /* hide until needed */
  position: fixed; /* fix to viewport */
  top: 0; /* place at top of viewport */
  left: 50%;
  transform: translate(-50%, 10px);
  max-width: 300px;
  width: calc(100vw - 20px);
  margin: 0 auto;
  padding: 10px 20px;
  background-color: #fbfbfb;
  border-radius: 10px;
  border: 1px solid #bbbbbb;
  box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.3);
  text-align: left;
}

/* close button for notification */
.closebtn {
  margin: -15px -15px 10px 10px;
  padding: 10px;
  color: #888888;
  font-weight: bold;
  float: right;
  font-size: 1.5em;
  cursor: pointer;
  transition: 0.3s;
}

/* hover effect for close button */
.closebtn:hover {
  color: #000000;
}

/* .screen class applies to all screens */
.screen {
  max-width: 480px; /* mimic largest phone width */
  width: 100vw; /* width of viewport */
  height: calc(100vh - 4.5em); /* height of viewport minus height of #navigation menu */
  margin: 0 auto;
  padding: 20px 10px;
  overflow: auto;
  border: 1px solid #888888;
  /* can add other CSS for all screens, such as background-color, etc. */

}

/* show #screen1 when app first starts */
#screen1 {
	display: block;
}

/* hide other screens when app first starts */
#screen2, #screen3, #screen4 {
	display: none;
}

/* can add custom CSS for each specific screen */
#screen1 {

}

#screen2 {

}

#screen3 {

}

#screen4 {

}

/* #navigation menu fixed to bottom of viewport */
#navigation {
  position: fixed; /* fix to viewport */
  bottom: 0; /* place at bottom of viewport */
  left: 50%;
  transform: translate(-50%, 0);
  max-width: 480px; /* mimic largest phone width */
  width: 100vw; /* width of viewport */
  height: 4.5em;
  text-align: center;
  background-color: #ffffff;
  border: 1px solid #888888;
}

/* nav menu options */
nav > a {
	display: inline-block;
	/* for max-width and width, divide by number of screens */
	max-width: calc((480px / 4) - 4px);
	width: calc((100vw / 4) - 4px);
	margin: 0;
	padding: 0.5em 0;
	text-align: center;
	background-color: #ffffff;
	color: #888888;
	transition: 0.3s;
}

/* hover effect for nav menu options */
nav > a:hover {
	background-color: #eeeeee;
}

/* .active class indicates current screen within nav menu */
nav > a.active {
	background-color: #ffffff;
	color: #0099ff;
}

/* nav menu icon label */
nav > a > p {
	font-size: 0.75em;
	margin: 0.5em 0 0;
}

/* can add CSS for other elements, classes, or IDs */

```

This CSS styles certain elements, classes, and IDs within your web app. However, you can modify some of this CSS if desired.

You'll typically want to add CSS to style other HTML elements in your web app, in order to produce the desired layout and appearance for your app's user interface.

## JS

You can use this starter code for your JS file named `script.js`:





{% hint style="danger" %}
**IMPORTANT:**  You **must** modify this JS code to insert your actual Photon device ID and access token. Otherwise, your web app will **not** work properly.
{% endhint %}

This JS creates a new `Particle()` object and assigns it to a global variable named `particle`. This object has built-in methods \(functions\) that can be used to interact with your Photon device through Particle Cloud.

This JS also declares global variables to store your Photon device ID and access token. You must modify these lines to list [your actual device ID and access token](particle-cloud/web-app-prep-steps.md#device-id-and-access-token), which you will need to get from your team's Particle Build account.

Then you'll need to add the other necessary JS for your web app. Because your HTML file loaded the Particle API JS library and jQuery JS library, you can include Particle statements and jQuery statements within your JS code.

Review the reference section on [Particle Cloud](particle-cloud/) to learn how to make your web app JS interact with your Photon device app.

