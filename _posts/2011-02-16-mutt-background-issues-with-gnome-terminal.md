---
layout: post
title: 'Mutt transparent background issues with gnome terminal'

---

I recently decided that I would give Mutt a go, and can already see its benefits after a short trial.
Only thing was that it looked so ugly! 50% grey solid background and white text?? Turns out it has issues with transparency in gnome terminal.

Here is how to solve it, and have a transparent background in Mutt.

Simply put this line in your ~/.bashrc
<strong><span style="color: #ff6600;">export COLORFGBG="default;default"</span></strong>

Then refer to the transparent background as "default" in your ~/.muttrc, such as the example below
<span style="color: #ff6600;"><strong>color normal green 		default</strong></span>
