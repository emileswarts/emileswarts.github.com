---
layout: post
title: 'my most used mutt commands'

---


My mostly used Mutt commands

<pre>
	j &#8211; down
	k -  up
	
	* &#8211; go to last message
		--for easier reach, remapped in .muttrc with: bind index J    last-entry
		<br />
	= &#8211; go to first message
	5 &#8211; go to message with index of number 5
	&lt;return&gt; display message
	&lt;space&gt; page down within message
	&lt;tab&gt; &#8211; jump to next new message
	@ &#8211; show authors full email address ~cool
	a - Add to addresbook ~supacool
	r &#8211; reply to message
	f &#8211; forward message
	w &#8211; set status flag
	l &#8211; show messages matching a pattern
	F &#8211; mark as important
	m &#8211; new message
	N &#8211; Toggle new status
	v &#8211; view attachemnts mode
	q &#8211; exit
	&lt;c-g&gt; &#8211; cancel current operation
	d &#8211; mark message for deletion
	u &#8211; undelete message
	C &#8211; copy message to another folder
	c &#8211; change directory
	o &#8211; reverse sort order
	t &#8211; toggle tag on message
	T &#8211; tag messages with matching pattern (&lt;c-t&gt;) untag
	/ &#8211; search forward
	&lt;alt-/&gt; &#8211; search backwards
	Limiting
	l ~d 21/1/99-25/2 -All messages with date between 21 Jan 1999 and 25 Feb 1999
	l ~d&lt;1d &#8211; Messages within last day
	l ~d 15/1/2001*2w &#8211; All messages plus minus two weeks old from 15 Jan 2001
	Quick Mutt emails
	mutt -s &#8220;testmail&#8221; emile@fatbeehive.com -a &#8216;/home/korpz/.mutt/aliases&#8217; &lt; &#8216;test body content&#8217; ~You know you need this
	
	Quick limit
	~d 15/1/2011 ~f johnLimit messages to a specific date, and from
</pre>
