---
layout: post
title: 'Benchmarking with apache2-utils'
description: Benchmark your website.

---


Get apache2-utils
<pre>
sudo pacman -Syu apache2-utils
</pre>

Run benchmark test, don't forget the trailing slash
<pre>
ab -c 1 -n 50 http://www.yourtestsite.com/
</pre>
