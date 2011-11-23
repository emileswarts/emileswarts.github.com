---
layout: post
title: 'Modify taglist plugin'

---


<p> Taglist.vim is an awesome plugin that displays all the functions, variables, constants, classes for open files.
	In my case, I did not want to see only the functions for php. You can easily modify this. 
	To do this, open your taglist plugin.  </p>

<pre>/home/user/.vim/bundle/taglist.vim/plugin/taglist.vim</pre> 
//I am using the pathogen plugin, so your path might be a bit different. </em></strong></span></p>
Locate the following line:

<pre> let s:tlist_def_php_settings = 'php;c:class;d:constant;v:variable;f:function'</pre>

Remove constants and variables

<pre> let s:tlist_def_php_settings = 'php;c:class;f:function' </pre>
