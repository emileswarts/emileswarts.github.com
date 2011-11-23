---
layout: post
title: 'Multiple user keyboard layouts linux -Colemak'

---


I recently decided to move away from the QWERTY layout to try Colemak.  I work on a lot of remote servers though, and needed a way to setup Colemak on them for just my user profile.  Follow the instructions below to do this:

Create ~/.xinitrc on your remote server.
This file will let you switch between the two keyboard layouts.

Add the following to this file:

<pre>
	#setxkbmap us; xset -r 66
	setxkbmap us -variant colemak
</pre>

Notice that the qwerty one is the one on top that has been commented out.
Add the following to your ~/.bashrc

<pre>
source ~/.xinitrc
</pre>
