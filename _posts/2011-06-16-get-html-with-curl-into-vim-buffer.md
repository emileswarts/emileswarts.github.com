---
layout: post
title: 'Get html with curl into vim buffer'

---


Get entire html page with curl and write it to a buffer in vim.
This is useful for when you need to get data from a site and you dont want to reach all the way over to the mouse :)

 <pre>
	 :r !curl http://rest/service --request POST --data @%
 </pre>

Then strip out the tags
-----------------------

 <pre>
	 :%s/<[^>]*>//g
 </pre>

magic

