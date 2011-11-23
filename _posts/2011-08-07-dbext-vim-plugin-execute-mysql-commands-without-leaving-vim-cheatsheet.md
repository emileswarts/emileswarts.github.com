---
layout: post
title: 'Dbext VIM plugin - Execute mysql commands without leaving vim - cheatsheet'

---


I recently found the Dbext plugin by Peter Bagyinszki, which eliminates the need for me to have to type out manual mysql queries on the command line.
It enables you to save a file with commonly used queries, and then run them with a simple shortcut.

I will not go into depth about this plugin, and you can learn more about it by downloading it here:

<a href="http://www.vim.org/scripts/script.php?script_id=356" target="_blank">http://www.vim.org/scripts/script.php?script_id=356 </a>

I would recommend reading the documentation, and doing the quick tutorial that is provided with it.

My leader key has been set to , 

Shortcuts

Show buffer parameters.  Prompt for configuration for you database connection
<pre>,sbp </pre>

Same as
<pre>: DBPromptForBufferParameters</pre>


Execute a command on a line that your cursor is on
<em>Create a file with your most used commands</em>
<pre>,sel - mnemonic for: s(sql)e(execute)l(line)</pre>


Execute visually selected text
<pre>,se - mnemonic for: s(sql)e(execute)</pre>


This will select * from prompted table
<pre>,sta  - mnemonic for: s(sql) t(table) a(ask name) </pre>


Describe table with visually selected table-name
<pre>,sdt - mnemonic for: s(sql)d(describe)t(table)</pre>


Show history (can execute commands from this buffer)
<pre>,sh - mnemonic for: s(sql)h(history)</pre>

Change options (I use this mostly to switch databses)
<pre>:DBSetOption user|passwd|dsnname|srvname|dbname|host|port|...=<value></pre>

