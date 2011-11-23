---
layout: post
title: 'preg_replace to grab and rewrap html'

---

I will be demonstrating a fairly simple example using php preg_replace with HTML.  I got stuck on this today, and decided to document my research to use this as future reference.

Problem: Automate accordion on content pulled from a content managed system.  Only requirement from the client is that they create consecutive h2 tags, with content in between them.

I need the following HTML to be generated:
<pre>
&lt;div id=&#34;accordion&#34;&gt;
&lt;h2&gt;Title&lt;/h2&gt;
&lt;div&gt;
&lt;p&gt;content&lt;/p&gt;
&lt;/div&gt;
&lt;/div&gt;
</pre>

preg_replace works is the tool for the job, and this is the code that I used.

Modifiers:
i - case insensitive
m - multiline  ~this was what I did not include, and got stuck.
s - . character matches all characters

$pattern = &#34;/&lt;\/h2&gt;(.*?)&lt;h2 ([^&gt;]*?)&gt;/ism&#34;;
$replace = &#34;&lt;/h2&gt;&lt;div&gt;$1&lt;/div&gt;&lt;h2 $2&gt;&#34;;

return(preg_replace($pattern, $replace, $content));
