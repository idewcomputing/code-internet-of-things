# Web App - Multiple Screens

You can also create a multi-screen web app that interacts with your Photon device through Particle Cloud. Your multi-screen web app will consist of an HTML file named`index.html`, a CSS file named `style.css`, and a JavaScript file named `script.js`.

Your web app will be a [single-page application](https://en.wikipedia.org/wiki/Single-page_application) that dynamically shows different "screens."  Your web app will only have one HTML page, but different `<div>` sections in the HTML will represent different screens. Your web app will only display one specific `<div>` screen at a time, while hiding the other `<div>` screens.

This section contains starter code that you can use for your HTML, CSS, and JS files. You'll need to add to the starter code \(and modify certain parts\).

This starter code has been designed to mimic the appearance and interaction of a native mobile app. An icon-based navigation menu will be displayed at the bottom of the page to allow the user to switch between screens to perform different tasks or view different information.

By default, this app code is designed to show 4 different screens \(but you can modify the code to change the number of screens\). This app code also has a `<div>` section that can be use to display an incoming push notification from your smart device.

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

At the beginning of the &lt;body&gt; section, there is a &lt;div&gt; section with the id name of "notification" that will can be used to display an incoming push notification message from your smart device. 

#### DIV FOR EACH SCREEN

In the `<body>` section, there are several blank lines are where you will add HTML for your web app.  \(You can use more lines, obviously.\)  This is where you might display text, images, links, buttons, etc.

#### NAV FOR SCREEN MENU

Towards the end of the 

#### LOAD JAVASCRIPT FILES

At the bottom of the `<body>` section, there are `<script>` tags to load several JavaScript files into your web app:

1. Particle API JS library:  `particle.min.js`
2. jQuery JS library:  `jquery.min.js`
3. Your web app JS file:  `script.js`

The [Particle API JS library](https://docs.particle.io/reference/javascript/) contains methods to allow your web app to interact with your Photon device through Particle Cloud. You'll use Particle methods in your web app JS file.

The [jQuery JS library](https://api.jquery.com/) contains methods that make it easy to modify the content and style of your web app by dynamically changing its HTML and CSS. You'll use jQuery methods in your web app JS file.

## CSS

You can use this starter code for your CSS file named `style.css`:



This CSS styles the `<body>` section of your web app. However, you can modify this CSS if desired.

You'll typically want to add CSS to style other HTML elements in your web app, in order to produce the desired layout and appearance for your app's user interface.

## JS

You can use this starter code for your JS file named `script.js` \(be sure to modify\):





{% hint style="danger" %}
**IMPORTANT:**  You **must** modify this JS code to insert your actual Photon device ID and access token. Otherwise, your web app will **not** work properly.
{% endhint %}

This JS creates a new `Particle()` object and assigns it to a global variable named `particle`. This object has built-in methods \(functions\) that can be used to interact with your Photon device through Particle Cloud.

This JS also declares global variables to store your Photon device ID and access token. You must modify these lines to list [your actual device ID and access token](particle-cloud/web-app-prep-steps.md#device-id-and-access-token), which you will need to get from your team's Particle Build account.

Then you'll need to add the other necessary JS for your web app. Because your HTML file loaded the Particle API JS library and jQuery JS library, you can include Particle statements and jQuery statements within your JS code.

Review the reference section on [Particle Cloud](particle-cloud/) to learn how to make your web app JS interact with your Photon device app.

