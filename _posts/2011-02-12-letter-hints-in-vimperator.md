---
layout: post
title: 'letter hints in vimperator'

---

I recently found Vimium for Google Chrome, and decided to give it a testdrive.
After 5 minutes, I was pretty impressed but found that it was just not as comprehensive
as Vimperator.

What Vimium did have that Vimperator lacked(in the default settings),
was letter hints.  It is much easier to use, and there is no need to take your
fingers off the home row most of the time.

To use letter hints instead of numbers, add the plugin found on the url below in your ~/.vimperator/plugin directory.
http://coderepos.org/share/browser/lang/javascript/vimperator-plugins/trunk/char-hints-mod2.js

Then add the following line to your .vimperatorrc file
let g:hintsio="iO"
