---
layout: post
title: Control Spotify from the command line
description: This basic python script allows you to send instructions to spotify to skip tracks.

---

<p>
	I am often working on something, only to get distracted by a terrible track which was selected through related artists, or Spotify radio.  This does
	not happen too often, but it does happen and I would like a quick way to skip the track without having to mess with the GUI.  I searched online for something that could do this but after half an hour I had still not found anything.  
</p>

<p>To get this working, you need to install xdotool.  You will also need Python installed.</p>
<p>This example will be for linux, but should work fine on any unix like system.</p>

<p><pre>sudo pacman -S xdotool</pre></p>

<p>Once that is done, you can copy the script below and place it somewhere in your path.  Mine resides in ~/bin/spotify.py</p>


<pre>
import subprocess
import sys

def sendkeys(*keys):
	subprocess.call(['xdotool', 'search', '--name', 'Spotify Premium - Linux Preview', 'key'] + list(keys))
	return "ok\n"

if sys.argv[1] == 'n':
	sendkeys('ctrl+Right')
elif sys.argv[1] == 'p':
	sendkeys('ctrl+Left')
</pre>

<p>Make sure to give it executable permissions.</p>

<p><pre>chmod +x ~/bin/spotify.py</pre></p>

<p>So you would envoke this from the command line as follows:</p>

<p><pre>python ~/bin/spotify.py</pre></p>

<p>As an additional convenience, you can alias this to a shortcut.</p>

<p>
<pre>
echo "alias n='python ~/bin/spotify.py n'" >> ~/.bash_aliases
echo "alias p='python ~/bin/spotify.py p'" >> ~/.bash_aliases
</pre>
</p>

<p>Reload your shell, and you should be able to press n, or p followed by enter to skip tracks.</p>
