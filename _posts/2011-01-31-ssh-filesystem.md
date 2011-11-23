---
layout: post
title: 'SSH Filesystem'

---

<h3>sshfs allows you to mount your remote server as a local drive.</h3>
Install
<span style="color: #ff6600;"><strong><em>sudo apt-get install sshfs</em></strong></span>

Configure<a title="SSHFS" href="http://fuse.sourceforge.net/sshfs.html" target="_blank"><span style="color: #33cccc;">
http://fuse.sourceforge.net/sshfs.html</span></a>

Mount
<strong><span style="color: #ff6600;"><em>sshfs user@host.com:/home/user/stuff /home/user/site/</em></span></strong>

Unmount
<pre><strong><span style="color: #ff6600;">fusermount</span></strong><strong><span style="color: #ff6600;"><em><span style="color: #ff6600;"> </span>-u -z /home/user/site</em></span></strong> <span style="color: #99cc00;">-u unmount -z lazy mode</span></pre>
