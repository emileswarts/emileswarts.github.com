---
layout: post
title: 'Use less as pager for mysql'
description: 'Use a different pager in mysql'

---

When selecting huge chunks of data from a mysql database, you usually have to scroll up with the mouse to view the top entries.
To keep your hands on the keyboard, and even on the home row is good.

<pre>mysql&gt; pager less</pre>

If you wanted to manipulate the data, or copy something, you could use vim/emacs/nano as the pager
