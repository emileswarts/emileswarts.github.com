---
layout: post
title: 'Load Colemak layout on startup'

---



Create ~/.xinitrc in your home directory.

Add the following:

<pre>setxkbmap us -variant colemak </pre>
<br />

Add the following to your ~/.bashrc

<pre>source ~/.xinitrc </pre>
