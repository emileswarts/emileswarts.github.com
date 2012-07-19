---
layout: post
title: 'SSH Filesystem'

---

sshfs allows you to mount your remote server as a local drive using fuse.

Install fuse
<pre>pacman -S sshfs</pre>

Configure
<pre>http://fuse.sourceforge.net/sshfs.html</pre>

Mount
<pre>sshfs user@host.com:/home/user/stuff /home/user/site/</pre>

Unmount
<pre>fusermount -u -z /home/user/site -u unmount -z lazy mode</pre>
