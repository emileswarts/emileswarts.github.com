---
layout: post
title: 'Dbext VIM plugin - Execute mysql commands without leaving vim - cheatsheet'
description: I recently found the Dbext plugin by Peter Bagyinszki, which eliminates the need for me to have to type out manual mysql queries on the command line and keeps you in vim.

---

I recently found the Dbext plugin by Peter Bagyinszki, which eliminates the need for me to have to type out manual mysql queries on the command line and keeps you in vim.
It enables you to save a file with commonly used queries, and then run them with a simple shortcut.

I will not go into depth about this plugin, and you can learn more about it by downloading it here:

http://www.vim.org/scripts/script.php?script_id=356

I would recommend reading the documentation, and doing the quick tutorial that is provided with it.

My leader key has been set to ,

Shortcuts

Show buffer parameters.  Prompt for configuration for you database connection
```
,sbp
```

Same as

```
: DBPromptForBufferParameters
```

Execute a command on a line that your cursor is on
Create a file with your most used commands

```
,sel - mnemonic for: s(sql)e(execute)l(line)
```

Execute visually selected text

```
,se - mnemonic for: s(sql)e(execute)
```

This will select * from prompted table

```
,sta  - mnemonic for: s(sql) t(table) a(ask name)
```

Describe table with visually selected table-name

```
,sdt - mnemonic for: s(sql)d(describe)t(table)
```

Show history (can execute commands from this buffer)

```
,sh - mnemonic for: s(sql)h(history)
```

Change options (I use this mostly to switch databses)

```
:DBSetOption user|passwd|dsnname|srvname|dbname|host|port|...=<value>
```

