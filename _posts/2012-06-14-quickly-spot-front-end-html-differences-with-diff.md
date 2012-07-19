---
layout: post
title: 'Diff is your friend'

---

Diff is generally thought of as being a file related command.
Lucky for us, everything is a file in a unix environment. 
Here are a few diff functions that I find really useful.

If you work on a website, and want to see the final html difference between production and test then you can run the following.  If you wanted to clean up the output, you could pipe the curl command through the tidy program.

<pre>diff -u <(curl www.yoursite.com) <(curl localhost/yoursite) |view -</pre>

You could check the differences of a process.
<pre> diff -u <(ls) <(ls -lrt) |view -</pre>
