---
layout: post
title: 'Favorite linux  commands'

---



Favourite linux commands

Notify script for watching files as they grow.
<pre>tail -f /var/log/messages | while read line; do accu=&#8221;$line&#8221;; while read -t 1 more; do accu=`echo -e &#8220;$accu\n$more&#8221;`; done; notify-send &#8220;Syslog&#8221; &#8220;$accu&#8221;; done </pre>

Set reminder, and send it to the background
<pre>sleep 30m &amp;&amp; notify-send -t 10000 -u critical &#8220;do stuff&#8221; &amp; </pre>

Random command from commandlinefu.com &#8211; cool
<pre>lynx &#8211;dump http://www.commandlinefu.com/commands/random/plaintext | grep .  </pre>

List directories only
<pre>ls -d */ </pre>

Mail contents of file
<pre>mail -s &#8220;subject&#8221; youremail@mail.com &lt;/home/user/somedata.txt  &#8212; -f youremail@mail.com -F &#8216;John smith&#8217;; </pre>

Check version
<pre>cat /etc/issue </pre>

manage cron
<pre>crontab -e </pre>

clean up filename
<pre>detox filename //might need to install sudo apt-get install detox </pre>

grab screencast
<pre>ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/out.mpg </pre>

List by date
<pre>ls -lat</pre>

Replace typo in previous command
<pre>^typo^new^ </pre>

Remove all but important.html from current directory
<pre>rm -f !(important.html) </pre>

Remove all files except type txt or php
<pre>rm !(*.txt|*.php) </pre>

Change file permissions to be same as other file
<pre>chmod --reference file1 file2 </pre>

mysql operations without entering mysql mode, and show databases starting with e 
<pre>mysql -u user -h localhost -p -e "show databases;" | grep '^e' </pre>

Create multiple directories at once
<pre>mkdir -p dir1/dir2 </pre>

Grep only certain files with find
<pre>find . -name "*.css" -exec grep -l "#content" {} \; </pre>

Find files modified in the last day
<pre>find . -ctime -1 -type f </pre>

Find files newer than myfile
<pre>find ~/src -newer myfile.txt </pre>

Go home!
<pre>cd</pre>

monitor mysql processes
<pre>watch -n 1 mysqladmin --user=user --password=password processlist</pre>

change file permissions like other file 
<pre>chmod --reference file.txt otherfile.txt</pre>
