---
layout: post
title: 'Benchmarking with apache2-utils'
description: Benchmark your website.

---


Get apache2-utils
```
sudo pacman -Syu apache2-utils
```

Run benchmark test, don't forget the trailing slash
```
ab -c 1 -n 50 http://www.yourtestsite.com/
```
