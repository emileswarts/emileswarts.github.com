---
layout: post
title: 'vim plugin - yankring'
description: Yankring is a great plugin.  You can access it quickly by mapping it to a key. 

---


Yankring is a great plugin.  You can access it quickly by mapping it to a key as shown below.
I never really fully utilized the registers in VIM, but
decided to get it correct with the Yankring plugin.

Open Yankring

<pre>:YRShow&#60;CR&#62; </pre>
<br />

add to .vimrc
<br />

<pre>nnoremap &#60;leader&#62; r :YRShow &#60;CR&#62; </pre>



