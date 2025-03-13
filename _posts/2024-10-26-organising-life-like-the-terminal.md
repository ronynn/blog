---
layout: post
title: Organising life like I organise my bashrc file
categories: [Design, Philosophy]
image: https://ronynn.github.io/assets/images/zsh.jpg
author: ronynn
---

Returning to a project after a long hiatus is akin to discovering a hidden room in your house, one you’d long forgotten. Imagine, if you will, the mess that greets you—a chaotic collage of old notes, disorganized cables, and half-empty coffee cups. It’s a familiar scene, one that many of us encounter. We live in cramped spaces, both physical and digital, where the ideal of a separate workspace for every endeavor is a luxury few can afford. In the face of such clutter, a methodical approach to organizing—be it on your desk or your computer—becomes a necessity.

The desk, a faithful witness to countless hours of toil, often becomes a battleground of forgotten projects. The half-finished manuscripts, scattered sketches, and neglected to-do lists create a landscape of past aspirations. Yet, the real challenge is not in the mess itself but in the mental map we’ve built around it. A messy desk isn't necessarily a signal of disorganization if you’ve mapped out the chaos in your mind.

> **"A cluttered desk is a sign of a cluttered mind; but a cluttered mind can sometimes be a treasure trove of creativity."** —Anonymous

In the realm of digital clutter, the computer’s hard drive, much like the physical desk, accumulates a mélange of files, folders, and fragments of bygone projects. In an ideal world, each project would have its dedicated space, neatly partitioned to prevent overlap. However, most of us are constrained by limited disk space and the more mundane realities of modern life. Thus, files become intermingled, creating a digital labyrinth that can be daunting to navigate.

To address this digital disarray, one ingenious solution I’ve found is embedded in something as unassuming as a `bashrc` file. Yes, you read that right—a simple configuration file used by the Unix shell. For those unacquainted, the `bashrc` file is where you can set environment variables, customize your shell prompt, and, importantly, create shortcuts to frequently used directories.

By keeping a mental map of my disk space in this unpretentious file, I managed to streamline my return to old projects. Each time I embarked on a new endeavor, I’d update my `bashrc` with paths to critical folders, shortcuts to tools, and notes on what each directory contained. When the time came to revisit an old project, this file became my map, guiding me swiftly through the cluttered digital landscape.

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

This approach is more than a mere practical solution; it’s a philosophical stance on organization. It’s not about achieving perfection in tidiness but about creating a system that works for you, one that allows you to navigate the mess with ease. It’s akin to a mental map—an abstract representation that makes the chaos comprehensible and manageable.

Reflecting on this, one can draw parallels to life itself. Much like a cluttered desk or a disorganized hard drive, our lives are often filled with overlapping commitments, forgotten dreams, and unspoken aspirations. We live in an era where our time and energy are stretched thin, making it impractical to keep every aspect of our lives neatly compartmentalized.

Yet, the essence of managing such complexity lies not in achieving a state of perfect order but in developing a system that allows us to keep track of what matters. Just as I used my `bashrc` file to create shortcuts and maintain a mental map of my digital world, we can apply similar principles to our personal lives.

Consider the notion of creating a mental or physical “map” of your life’s projects and responsibilities. This could be as simple as a journal where you jot down goals, deadlines, and reflections. It could be a digital tool where you track various aspects of your life, or even a well-organized planner. The objective is not to eliminate the mess but to develop a system that helps you navigate it effectively.

In essence, the key to managing both physical and digital clutter lies in understanding that chaos is inevitable. The real challenge is to create a system that allows you to find what you need when you need it. The `bashrc` file is but a humble example of how such systems can be implemented with minimal fuss. It is, of course, not the ultimate solution to life’s complexities, but it serves as a reminder that even in the midst of chaos, there can be a semblance of order.

To those who might find the analogy of a `bashrc` file to life’s organizational challenges a bit far-fetched, I extend my apologies. It’s a quirky comparison, but one that highlights the broader truth that order can be found in the most unexpected places. Whether through a digital file or a well-tended personal system, the essence remains the same: create a method that allows you to efficiently navigate the clutter and return to your projects with clarity.

In the end, whether you’re sifting through a messy desk or an overstuffed hard drive, the goal is to craft a system that transforms chaos into clarity. While my `bashrc` file might be an unconventional metaphor, it underscores the importance of finding personal solutions that work for you. Embrace the mess, make your map, and let creativity flow amidst the clutter.
