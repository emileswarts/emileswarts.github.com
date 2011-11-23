---
layout: post
title: 'Add git colours to your .gitconfig'

---


Add colours to your git statements 

<pre>$ git config color.ui true

[color]
  branch = auto
  diff = auto
  status = auto

[color "branch"]
  current = yellow reverse
  local = yellow
  remote = green

[color "diff"]
  meta = yellow bold
  frag = magenta bold
  old = red bold
  new = green bold

[color "status"]
  added = yellow
  changed = green
  untracked = cyan

[user]
  name = User Name
  email = user.name@something.com
</pre>
