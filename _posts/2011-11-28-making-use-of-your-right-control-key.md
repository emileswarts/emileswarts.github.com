---
layout: post
title: 'Remap ESC key Happy Hacking Keyboard II Linux Xmodmap'

---

I recently purchased the Happy Hacking keyboard Professional II which conveniently places the Control key where the Caps Lock key used to be, removing caps lock from the layout entirely. 

While this is great, on my other keyboard (being a VIM user) I had remapped Caps lock to be Esc which I got quite used to, and was especially convenient on the vi-mode command line for bash.  

By default on the happy hacking keyboard the escape key is pressed through a combination of &#60;cntrl&#62;&#91; which is akward to press in my opinion.;

I also got used to having the control key where caps lock used to be.

I decided to remap the right modifier key (next to the spacebar) to be esc, as this is a key that I never use and it is more conveniently placed and only requires the right thumb than the pinky combination.

The keycode for the right modifier key is 134, so we will add the following to our ~/.Xmodmap.

If it does not exist, create it.
 <pre> keycode 134 = Escape</pre>
