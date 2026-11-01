---
layout: post
title: Organising life like I organise my bashrc file
author: ronynn
---

I came back to a project I hadn’t touched in eight months and couldn’t find anything. The code was there. The notes were somewhere. The assets were in three folders with names like `final`, `final2`, and `old-final`. I spent an hour just figuring out where things were before I could start working.

That’s the normal state of a project you’ve abandoned. The desk version looks the same: old notebooks, cables, a mug, a stack of printouts you kept meaning to file. Most of us don’t have a separate room for every project, so the mess accumulates in the same place. The point isn’t to have a clean desk. The point is to be able to find things when you come back.

The desk, a witness to countless hours of toil, is a battleground of forgotten projects. The neglected to-do lists create a landscape of past aspirations. Yet, the real challenge is in the mental map we’ve built around it. A messy desk isn't necessarily a signal of disorganization if you’ve mapped out the chaos in your mind.

> **"A cluttered desk is a sign of a cluttered mind; but a cluttered mind can sometimes be a treasure trove of creativity."** —Anonymous, often attributed to Einstein too

The digital version is worse because you can’t see it. A disk fills up with folders from projects you finished, half-finished, or forgot about. In theory every project gets its own directory and everything stays partitioned. In practice you have one disk, a home directory, and a habit of putting things where they fit at the time.

![zsh](https://ronynn.github.io/blog/assets/images/zsh.jpg)

What helped me was my `bashrc`. If I add an alias every time I start a project, then the file becomes a list of the places I actually work. When I come back after a long break, I don’t have to remember the path. I just read the aliases.

Here’s the relevant part of my `bashrc` on termux:

```bash
shopt -s histappend
shopt -s histverify
export HISTCONTROL=ignoreboth

# Default command line prompt.
PROMPT_DIRTRIM=2
PS1='\[\e[0;32m\]\w\[\e[0m\] \[\e[0;97m\]\$\[\e[0m\] '

# Handles nonexistent commands.
# If user has entered command which invokes non-available
# utility, command-not-found will give a package suggestions.
if [ -x /data/data/com.termux/files/usr/libexec/termux/command-not-found ];
then
  command_not_found_handle() {
    /data/data/com.termux/files/usr/libexec/termux/command-not-found "$1"
  }
fi

alias c="cd ~/storage/shared/Music"
alias todocs="cd ~/storage/shared/documents"
alias brc="cd /data/data/com.termux/files/usr/etc/ && nano bash.bashrc"
alias motd="cd /data/data/com.termux/files/usr/etc/"
alias n="nano"
alias serve="esbuild --servedir=."
alias m="micro"
alias pp="cd .."
alias ll="ls -a"
```

<figcaption> A portion of my bashrc file on termux </figcaption>

The aliases are the map. `c` is where I keep music, `todocs` is documents, `brc` opens the config itself. If I start a new project, I add an alias for its directory. If I stop working on it, the alias stays. A year later I type `alias | grep projectname` or just look at the file and I know where it lives. No separate app, no bookmark system, no notes I’ll lose.

That’s the whole trick. It’s not a philosophy. It’s a file I already edit, used as a list of places I care about. The reason it works is that I don’t have to maintain a second system. The map is in the same place as the tools.

The life analogy is probably obvious by now. You have commitments, projects, and things you meant to do that don’t fit into neat categories. You can’t keep everything separated. What you can do is keep a small file — a journal, a planner, a text file, whatever you’ll actually open — with the paths to the things you need to find again. Not a perfect system. A map that works for you.

For me that’s `bashrc` for code and a plain text file for everything else. The text file has lines like `taxes -> folder, deadline April`, `dentist -> phone number, next appointment`, `book notes -> ~/notes/books.md`. It’s the same idea: write down where the thing is, not what the thing is. Then when you come back, you can find it.

The `bashrc` analogy is a bit much, I know. But it’s the example I actually use, and it’s small enough to copy. If you already have a file you open every day, put your map there. You don’t need a new app. You need a list of places, and a habit of adding to it when you start.

I can say it’s a philosophical stance on organization. It’s about creating a system that works for you and not just achieving perfection in tidiness, one that allows you to navigate the mess with ease.