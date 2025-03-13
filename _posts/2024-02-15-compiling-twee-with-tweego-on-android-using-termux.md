---
layout: post
title: Tutorial for compiling twee file on tweego using termux on android
categories: [Writing, Game Development]
author: ronynn
image: assets/images/php.jpg
---

In the second part of our tutorial we will get to a playable demo HTML interactive fiction game file.

Now that you have Termux and a text editor set up, it's time to install Tweego and download Twine story formats. This will lay the foundation for crafting immersive interactive fiction experiences.

*Installing Tweego*

Tweego is a command-line tool that converts Twine files into playable HTML games. To install Tweego, open Termux and navigate to your project folder:

```
cd mygame
```

Next, use the package manager to install Tweego:

```
pkg install tweego
```

This command will download and install Tweego, making it available for use in your project.

*Downloading Twine Story Formats*

Twine story formats are the backbone of your interactive fiction games. These formats provide the structure and functionality for player interaction. You can find them on <https://twinery.org>.

Unzip the folder and move them to the mygame folder.

The file structure should appear like this
```
mygame
|_storyformats
  |__sugarcube-2
     |_format.js
  |__harlowe-3
     |_format.js
|_gamename. twee
```

*Creating Your First Game File*

Open your text editor and navigate to your project folder:

Create a new file called "game.twee":

```
// game.twee
:: Start
You are standing at the entrance of a dark cave.
[[Go Inside]]
[[Run Away]]

```

This simple example demonstrates the basic structure of a Twine game file.

*Saving and Compiling Your Game*

Save your "game.twee" file and return to Termux:

```
cd mygame
tweego -f sugarcube-2 -o game.html game.twee
```

This command tells Tweego to use the Sugarcube 2 format and output the compiled game as "game.html". You will get an error stating your game has no IFID which makes each interactive fiction game unique, just copy the code as instructed in the terminal and paste in your game.twee. Then run this command again.

*Playing Your Game*

Open the generated "game.html" file in a web browser to play your interactive story. With pictures it won't be able to run on the browser and your would need to fire up a local server, simplest way to which is using python, it is however not needed for our project right now.

Congratulations! You've successfully set up Tweego and Twine story formats, and created your first interactive fiction game.

In the next part of this tutorial series, we'll explore:

Publishing your game online, and make an android app using it.

Stay tuned!

