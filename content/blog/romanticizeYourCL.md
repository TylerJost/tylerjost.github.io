---
title: "Romanticize Your Command Line"
date: 2025-12-20
draft: true
type: 'blog'
featured: false
tags: 
  - programming
  - personal
  - compbio
---

A lot of people find that the command line is intimidating, especially in the life sciences, and that's for a good reason. A black terminal with a blinking cursor is completely foreign to someone who is accustomed to a graphical interface. Even some some computational biologists don't *really* love the command line. They'd rather run everything out of a jupyter notebook and be done with it. But if you're serious about leveling up or just want a better experience with your computer, "romanticizing" your command line is one of the easiest ways to become more comfortable with your terminal experience. 

# Step 0: Convince Yourself This is Worth It
If you made it past the intro paragraph, I want to take the time to further explain why you should take the time to follow this guide. A while back, a friend gave me the advice that, in every situation, you should try to romanticize your life. Take the long walk through the park, walk up the stairs to see the sun set, and text your friends to say you care. To me, this beauty should also extend to your terminal, both in aesthetics and ease of use. 

My promise to you is that this will be the most batteries included tutorial I can provide. I've installed these programs on plenty of computers, and it's pretty much plug and play. 

# Step 1: Fix Your Terminal
### Goal: Make command line tools accessible by making the terminal easy to use, find, and execute. 
What terminal do you use? This is the first thing to get out of the way, and it's mostly for the Windows users. Not too long ago, there really weren't that many good options, but now there's only one and that's Windows Terminal. You probably have it installed already, but what we really want to do is [install WSL](https://learn.microsoft.com/en-us/windows/wsl/install). WSL (Windows System for Linux) will enable us to use all of the features of Linux on our Windows machine. If you're on Mac the default terminal is fine (just fine), but a more advanced terminal experience is usually recommended such as [iTerm](https://iterm2.com/) because it has more colors. 

# Step 2: Use ZSH as your shell
### Goal: Use a shell that gives you easy access to plugins to smooth out your experience. 

The [shell](https://en.wikipedia.org/wiki/Shell_(computing)) is what allows you to communicate with your machine. Currently, Macs use Zsh but WSL will start you off with Bash, and a lot of default shells for new Linux distros use Bash as well. I know this all sounds complicated, but basically we just want to have plugins and Zsh has them in spades. 