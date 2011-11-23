---
layout: post
title: 'Vim word frequency'

---

Put the following in your .vimrc

<pre>
function! WordFrequency() range
  let all = split(join(getline(a:firstline, a:lastline)), '\A\+')
  let frequencies = {}
  for word in all
    let frequencies[word] = get(frequencies, word, 0) + 1
  endfor
  new
  setlocal buftype=nofile bufhidden=hide noswapfile tabstop=20
  for [key,value] in items(frequencies)
    call append('$', key."\t".value)
  endfor
  sort i
endfunction
command! -range=% WordFrequency &lt;line1&gt;,&lt;line2&gt;call WordFrequency()
</pre>


Type 
<pre>
:WordFrequency 
</pre>

for a summary of the words
