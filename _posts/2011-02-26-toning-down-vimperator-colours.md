---
layout: post
title: 'Toning down vimperator colours'

---

When following links (hints) all day, depending on your colour scheme it can be very obtrusive.
It would change the colours of some of the elements on the page, such as input boxes and headings.

Modify your colourscheme file, <span style="color: #00ffff;"><em>eg. /home/emile/.vimperator/colors/yourcolourscheme.vimp</em></span>
Find the following line, and change the colours to none.
<span style="color: #ff6600;"><strong>hi HintElem             background-color: none; color: none;</strong></span>

Now following hints should just bring up the numbers, and not change the colours of the elements on the page.
