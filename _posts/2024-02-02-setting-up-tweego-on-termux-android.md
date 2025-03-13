---
layout: post
title: Setting up tweego in termux for developing Interactive Fiction Games on Android
categories: [Writing, Game Development]
author: ronynn
image: assets/images/php.jpg
---
In the first part of this tutorial series, I'll guide you through setting up Tweego in Termux, a powerful tool for crafting immersive stories on your Android device using twine storyformats with just a text editor outside the twine editor.

*What is Termux?*

Termux is a terminal emulator for Android, providing a Linux-based environment on your device. Think of it as a command-line interface, similar to those found on desktop computers. With Termux, you can:

- Run Linux commands and scripts
- Install packages and software
- Manage files and directories
- Access network services

This is where it becomes useful for running tweego which is a command line application that takes you game text written in twee format and uses the appropriate storyformat to generate a HTML file similar to what the twine editor does.

*Why Use Termux for Interactive Fiction?*

Termux offers several benefits for interactive fiction development:

- Flexibility: Run Tweego and other command-line tools, run older text adventures with tools like frotz.
- Portability: Develop on your Android device, anywhere. I personally found that I get more dialogue ideas when listening to people on the streets and thus most of my games were written when I was out.
- Customization: Tailor your environment to suit your needs
- Programming: Perhaps dive into other programming projects.

*Setting Up Termux*

Follow these steps to get started:

*Step 1: Installing Termux*

Visit the Google Play Store and download Termux. Even though the google play version has recently been updated, it is advised to download the apk from github or fdroid, to do that after clicking on the downloaded apk you phone would ask whether you wish to give your file manager app permissions to install apk files. Use an open source file manager to ensure it isn't installing arbitrary apks behind your back when you are not using your phone.

*Step 2: Launching Termux*

Open Termux, and you'll see a command-line interface. Your keyboard should be open if not click on the screen. To exit type exit and then hit enter key on your keyboard.

*Step 3: Updating and Upgrading Termux*

Run the following commands to update and upgrade the package list:

```
pkg update
pkg upgrade
```

This ensures you have the latest packages and security patches. This also ensures new installs can use the latest libraries needed for their functions, research more about the design of linux.

*Step 4: Creating a Development Folder*

Create a new folder for your project:

```
mkdir mygame
```

Navigate into the folder:

```
cd mygame
```

*Step 5: Setting Up Your Text Editor*

Choose a suitable text editor for creating your game, within termux you can immediately use nano or use a dedicated android text editor like:-

- ACode
- Squircle Editor
- Karbon (XED Editor)

Install your chosen editor.

*Configuring Your Text Editor*

Before proceeding, configure your text editor:

- Set the font size and style
- Enable syntax highlighting (if available)
- Familiarize yourself with the editor's interface

Some popular text editor settings:

- ACode: Settings > Editor > Font Size
- Squircle Editor: Menu > Settings > Text Size

Fiddle around your new text editor, navigate to the mygame folder and create a new text file with the twee format: gamename.twee

You could choose to use nano editor as well or download another terminal based text editor, for now you can  on the terminal input

```
nano gamename.twee
```

Another advantage with nano is that syntax highlighters for twee format exist for nano and not in any other android text editor.

You've successfully set up Termux and chosen a text editor! In the next part of this tutorial series, we'll explore:

- Installing Tweego
- Downloading Twine story formats
- Creating your first interactive fiction game

Stay tuned!

