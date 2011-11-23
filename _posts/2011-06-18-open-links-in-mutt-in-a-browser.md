---
layout: post
title: 'urlview for Mutt'

---


<p>urlview makes navigating links in text emails much easier.</p> 
<pre>sudo apt-get install urlview</pre> 
<br />To map it to a key, add the following to your <strong>~/.mutt/macros</strong> file, if it does not exist create it</p>

<pre>macro pager \cb <pipe-entry>'urlview'<enter> 'Follow links with urlview' </pre> 
Restart mutt and press cntrl b in index view to see a list of available URL's in the email.  
Press <CR> on the link to open it in a browser. <br />
