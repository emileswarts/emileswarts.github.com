---
layout: post
title: 'VIM cheatsheet'

---



YANKING
<pre>
"+y   //yank into system clipboard
      mapped ,y in .vimrc
"_y  //yank into black hole
yy  //yank line
</pre>


 MARKS
<pre>
ma  //mark a
'a  //go to mark a
</pre>

SEARCHING
<pre>
/something //search forwards for something, press n for next
?something //search backwards for something, press n for next
/something\|other //search forwards for something, OR other
/something\&other //search forwards for something, AND other
/\/ //search forwards Wordboundary.  Wont match johna..
\v //find exactly four numbers like 1234. Very magic mode
:g/span.*div/ //Display all line numbers for search results
</pre>

WORKING WITH MULTIPLE FILES
<pre>
:split filename  //split
:vsplit filename  //vertical split
:res -10  //reduce space of split window by 10 lines
:+   //increase split window by 1 line
:-   //reduce split window by 1 line
</pre>

TABS
<pre>
:tabe filename //file open in new tab
:tabc          //tabclose
 gf       //open filename under cursor
:tabn          //next tab
</pre>

ADVANCED NAVIGATION
<pre>
g; //previous position of edit
g, //next position of exit
W //next word by whitespace, not .,
H //head (top)
M //middle of file

:set number //display line numbers. mapped with n
:set list //show hidden characters.
need to change the colour
:set nonumber //turn off line numbers
</pre>

VISUAL MODE 
<pre>
vmotion //select letter under cursor plus motion
V //Visual line mode
gv //reselect last selected text
</pre>

LINE AND COLUMN HIGHLIGHTING
<pre>
,z         //highlight clolumn and line
mapped in ~/.vimrc with
nnoremap ,z set cursorline! cursorcolumn!
</pre>

Spelling
<pre>
:set spell
Check file type
:set ft?
Note taking
note  //bash alias for &#8216;vim ~/notes.txt&#8217;
,b //use selected for bk_debug
,bs //as above but wrap in quotes
,d  //die selected
,ds //wrap in quotes
</pre>

REGISTERS
<pre>
:let @a=@/  //copy last search command to register a, or whatever register.
</pre>

OTHER
<pre>
:%s=  *$==// delete end of line blanks
:%s/^\(.*\)\(\n\1\)\+$/\1/  // delete multiple duplicate lines --AWESOME
:sor  //Sort file
:vmap z :%s/\*\>/  //Pull visually highlighted text into lhs of substitute. --AWESOME
jj //escape insert mode. mapped in .vimrc with: inoremap jj 
g/^/.t //duplicate every line in file --wow
g/^error/ . w >> ~/home/errors.txt //match output to separate file
:g/^/exe ".w ".line(".").".txt" //each line of file extracted to file with line number as title
y:" //pull visuall selected text into commandline.  is control key R
:w !sudo tee % //Save when you forgot to sudo
</pre>

PLUGINS
List plugins
<pre>
:scriptnames
</pre>

NERD COMMENTER
<pre>
    http://www.vim.org/scripts/script.php?script_id=1218
    ,cm  //comment minimal
    ,cs  //sexy comment
    ,ci  //toggle comment
    ,cy  //yank and then comment - cool
</pre>

WRAP TAGS 
<pre>
VS   //good for html files
</pre>

SURROUND PLUGIN
<pre>
cs"'             //change surrounding from double quote to single
ds"'             //delete surrounding
dst              //delete surrounding tag
yss-             //surround content with php tags put this in .vimrc  -awesome
                      autocmd FileType php let b:surround_45 = ""
ysW(             //surround word with ( -awesome
vs(              //surround visual selection with ( -AWESOME
</pre>
