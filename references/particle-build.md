# Particle Build

## What's Particle Build?

​[Particle Build](https://build.particle.io/) is an online code editor \(web IDE\) provided by Particle. Particle Build is part of the Particle Cloud platform. You will use Particle Build to code and store all your Photon device apps.

The Photon device itself can only store and run **one** app at a time. However, you can create and save multiple apps in Particle Build. When you need to update the specific app stored on your Photon device, you'll do this in Particle Build – and your Photon will download the new app over Wi-Fi.

Your team will need a Particle account to log in to Particle Build. However, your teacher will most likely provide your team with an **existing** Particle account login \(email & password\) that's already associated with your specific Photon device. Every Photon has a unique device ID it uses to communicate with Particle Cloud, and each device ID can only be associated with one Particle account.

One person on your team should log in to Particle Build using your team's Particle account login.

Once you're logged in, you'll see the Particle Build code editor, which defaults to the "Code" menu and shows a blank app template.

![Particle Build User Interface](../.gitbook/assets/particle-build-ui.png)

The user interface for Particle Build is divided into 4 sections:

* On the far left is a vertical navigation bar with icons.
* On the middle left is a menu panel showing options for the current navigation selection.
* On the right side is the code editor panel showing the code for your current app.
* On the bottom of the code editor panel is a horizontal status bar that displays messages.

## Navigation Bar

If you hover your mouse pointer over an icon in the navigation bar, the icon's name will be displayed. Here is a summary of the navigation icons from top to bottom:

| Icon | Name | Purpose |
| :--- | :--- | :--- |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJEjLUFeSZqzdAdtK-C%2F-LJEjiwZZ_lGiFWTeLmW%2Fpb-flash-icon.png?alt=media&token=2a54eab6-7b96-4deb-ba85-c8b0eaa36263) | **Flash** | Flashes the current app to your Photon device over Wi-Fi \(The app will first be saved and verified. If there are errors in the app, it will **not** be flashed.\) |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJ0yqiO-iwEFiJVLk8K%2F-LJ10qTcnC_JJqBfpd6F%2Fpb-verify-icon.png?alt=media&token=ac805d27-665d-411c-bfc4-338f998b6123) |  **Verify** | Complies the current app to check for errors \(The app will first be saved.\) |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJ0pBBNm9hOWbswkZXP%2F-LJ0pSQvLOewPan-6Z_m%2Fpb-save-icon.png?alt=media&token=fad2b9de-0395-4646-b367-019766d499f2) | **Save** | Saves the current app in Particle Build |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LIwNMqkFJ7THEwQ2B-f%2F-LIwNurELJ40j6i39ApO%2Fpb-code-icon.png?alt=media&token=5e3f9393-a92c-400b-b51a-a060356c8c6e) | **Code** | Lists all your saved apps. Click an app's title to open it in the code editor. |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJKU-305XqNVnF_dEZR%2F-LJKVKuyKj68oqDFco7w%2Fpb-library-icon.png?alt=media&token=8fdbf2fd-fb83-44fc-80bb-6a7023de8f11) | **Libraries** | Lists libraries that can be included in your app to add functionality |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJKU-305XqNVnF_dEZR%2F-LJKVPgeuq7Oa7_8My_1%2Fpb-help-icon.png?alt=media&token=7733619b-be64-405d-87d3-95d9498f59d1) | **Help** | Lists quick help for device \(might not be available for your Photon\) |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJKU-305XqNVnF_dEZR%2F-LJKVTgQmUAvFJjG6Mt9%2Fpb-docs-icon.png?alt=media&token=688d3ade-0c50-436f-b7ff-2d07a7d8a7d2) | **Docs** | Opens new tab with Particle Reference Documentation for your device |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LIwKNV_UEEQb3F3giJN%2F-LIwKgW3kmSnG7D_92hv%2Fpb-devices-icon.png?alt=media&token=96850c7d-1462-4c89-b9c6-89c149c7a3d5) | **Devices** | Lists your devices. You can view the device ID, and signal device over Wi-Fi. \(If you have multiple devices, you can select which device to flash apps to.\) |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJKU-305XqNVnF_dEZR%2F-LJKVeI_JNwvES3gcsyk%2Fpb-console-icon.png?alt=media&token=93eb237e-c5ec-4dba-80c4-e69f4fba8b23) | **Console** | Opens new tab with Console showing your device's events in Particle Cloud |
| ​![](https://firebasestorage.googleapis.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LEGLBX3AeXb13IcoB4Q%2F-LJKU-305XqNVnF_dEZR%2F-LJKVjdTz4eSKH5K5gtK%2Fpb-settings-icon.png?alt=media&token=627c9785-78b2-49a9-a140-f4d0a1a0783e) | **Settings** | Provides options to: log out, change password, or get your access token. |

## Toggle the Menu Panel

The middle menu panel can be toggled between "show" and "hide" by clicking the same navigation icon repeatedly.

In general, you'll probably want to keep the menu panel shown – but if you want extra space for your code editor panel, you can temporarily hide the menu panel.  


