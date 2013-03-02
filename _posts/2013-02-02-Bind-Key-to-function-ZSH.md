---
layout: post
title: Map a key to a function ZSH and Oh My ZSH
description: To bind a function to a key combination, you need to create a widget for it and map it with bindkey.  In this example I will use Control e to execute ls -al, and print the current working directory.  

---


To bind a function to a key combination, you need to create a widget for it and map it with bindkey.  

In this example I will use Control e to execute ls -al, and print the current working directory.  
You could use whatever function you wanted.

In your custom directory in your oh-my-zsh setup (usually ~/.oh-my-zsh/custom/), create a script.  I called this one list_widget.zsh.

~/.oh-my-zsh/custom/list_widget.zsh

create the file and add the following code to it.  The echo is just to create a new line for reset prompt.

<pre>
	ls_wrap () {
		ls -al
		echo

		zle reset-prompt
	}

	zle -N ls_wrap

	bindkey "^e" ls_wrap
</pre>


Reload ZSH and by pressing Control e, it will execute pwd, and ls -al.