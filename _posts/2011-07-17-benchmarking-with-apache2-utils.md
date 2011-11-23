---
layout: post
title: 'Benchmarking with apache2-utils'

---


Get apache2-utils
<pre>
sudo apt get-install apache2-utils
</pre>

Run benchmark test, dont forget the trailing slash
<pre>
ab -c 1 -n 50 http://www.yourtestsite.com/
</pre>
