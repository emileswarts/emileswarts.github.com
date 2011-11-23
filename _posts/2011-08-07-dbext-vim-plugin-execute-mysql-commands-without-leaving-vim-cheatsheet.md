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

<pre>
<p>
Show buffer parameters.  Prompt for configuration for you database connection
<strong>,sbp </strong>
Same as
<strong>: DBPromptForBufferParameters</strong>
</p>
<p>
Execute a command on a line that your cursor is on
<em>Create a file with your most used commands</em>
<strong>,sel</strong> - mnemonic for: s(sql)e(execute)l(line)
</p>
<p>
Execute visually selected text
<strong>,se</strong> - mnemonic for: s(sql)e(execute)
</p>
<p>
This will select * from prompted table
<strong>,sta</strong>  - mnemonic for: s(sql) t(table) a(ask name) 
</p>
<p>
Describe table with visually selected table-name
<strong>,sdt</strong> - mnemonic for: s(sql)d(describe)t(table)
</p>
<p>
Show history (can execute commands from this buffer)
<strong>,sh</strong> - mnemonic for: s(sql)h(history)
</p>
<p>
Change options (I use this mostly to switch databses)
<strong> :DBSetOption user|passwd|dsnname|srvname|dbname|host|port|...=<value> </strong>
</p>
</pre>

