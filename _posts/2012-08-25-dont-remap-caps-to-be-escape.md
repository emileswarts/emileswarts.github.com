---
layout: post
title: "Don't remap caps-lock to be escape - waisted real estate, for the fussy keyboard connoisseurs"

---


tl;dr
------
Escape can be used for one function, control can be used for many.
-------------------------------------------------------------------

I used to have caps lock mapped to escape.  

I switched to colemak a while ago, and have never looked back at the qwerty mess that I left behind.  Trust me, qwerty was designed to be broken and
this becomes clear when using a different keyboard layout.

As far as operating systems go, I am a happy linux user but recently crossed paths with osx.

Since there is no xmonad on osx, I decided to try tmux.

When I first tried it though, I found the default modifier key combination to be rather awkward.  Especially if you are on a macbook.

<img src = 'http://localhost:4000/images/macbook_air_keyboard.jpg' style="float:left;padding-right:20px"/>

C-b as a default modifier is not easy to reach.  I use vim and all of my most used applications have vi-like key bindings.

Vim was designed for qwerty unfortunately, not colemak.  I was not going to change the meaning of keys to try change this with something like colemak.vim.  
I would rather burn the new keys into my fingers and keep it pure.  And that is what I did. There was room for improvement however.

In colemak, no key combination on the home row can really be used as an easy escape key as the combinations are used frequently in the English language.

For instance in qwerty, a lot of people have something like this below mapped to esc in vim.
"jk" or "jj"

On Colemak the equivalent of "jk" would be "en".  Not a good idea because too many words contain this sequence in English.  Same goes for most other home row combinations.

For this reason, I had escape mapped to Caps-lock.  This works great on the command line and you can just tap it to get back to normal mode, if you use
vi mode (set -o vi).  Same obviously goes for vim, and any other vi like applications.  While this is still not as good as the qwerty "jk" it worked fine.
(This is not a total loss, as the keys on the homerow are replaced with other ones such as n for next match under the right index finger)

So the control key was never fully utilized or even remapped.  It remained in its awkward position at the bottom of my keyboard.

I realized that ctrl chording would not be as bad if it was placed on the caps lock key.  I could just use the default 'ctrl \[' escape key which should be available as a default.

Also considering that Esc has 1 function and ctrl can have copious amounts of combinations.  It seems illogical to have it mapped the way I did.

So I remapped the caps-lock key to be ctrl and, not escape.  This worked great, and I found myself using the ctrl key more and more often.
Things like control-x control-l for sentence completion, and control-n for word completion joined the list of some of my mostly used commands.  Features that were once rarely used.  Not to mention the other tons of control mappings in vim.

Needless to say that Tmux also became much easier to manage.  control-a j, control-a k etc.
I worked with this layout for a few weeks and then even went a bit further by adding the "tn" insert mode escape sequence in vim.
On colemak, t is on the left index finder and n is on the right index finger.

I found tn to be a good shortcut, and rarely used in english.  I also liked the feel of using both index fingers to escape to normal mode.

Bottom line is that it is much more efficient to have caps remapped to control than it is to have it for escape. 
