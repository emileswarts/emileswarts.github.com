---
layout: post
title: 'Favorite linux  commands'

---



Favourite linux commands

<pre>
Notify script for watching files as they grow.
tail -f /var/log/messages | while read line; do accu=&#8221;$line&#8221;; while read -t 1 more; do accu=`echo -e &#8220;$accu\n$more&#8221;`; done; notify-send &#8220;Syslog&#8221; &#8220;$accu&#8221;; done

Set reminder, and send it to the background
sleep 30m &amp;&amp; notify-send -t 10000 -u critical &#8220;do stuff&#8221; &amp;

Random command from commandlinefu.com &#8211; cool
lynx &#8211;dump http://www.commandlinefu.com/commands/random/plaintext | grep .

List directories only
ls -d */

Maill contents of file
mail -s &#8220;subject&#8221; youremail@mail.com &lt;/home/user/somedata.txt  &#8212; -f youremail@mail.com -F &#8216;John smith&#8217;

Check version
cat /etc/issue

manage cron
crontab -e

clean up filename
detox filename //might need to install sudo apt-get install detox


grab screencast
ffmpeg -f x11grab -s wxga -r 25 -i :0.0 -sameq /tmp/out.mpg

List by date
ls -lat

Replace typo in previous command
^typo^new^

Remove all but important.html from current directory
rm -f !(important.html)

Remove all files except type txt or php
rm !(*.txt|*.php)

Change file permissions to be same as other file
chmod --reference file1 file2

mysql operations without entering mysql mode, and show databases starting with e 
mysql -u user -h localhost -p -e "show databases;" | grep '^e'

Create multiple directories at once
mkdir -p dir1/dir2

Grep only certain files with find
find . -name "*.css" -exec grep -l "#content" {} \;

Find files modified in the last day
find . -ctime -1 -type f

Find files newer than myfile
find ~/src -newer myfile.txt

Go home!
cd
</pre>
