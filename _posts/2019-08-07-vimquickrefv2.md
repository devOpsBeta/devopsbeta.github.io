---
layout: post
title:  "Vim Quick Reference v2"
date:   2019-08-07 21:43:04 -0500
categories: vi, vim, linux
permalink: /linux/vim
---

## from command mode:
```
:x! - to write and exit - same as :wq! 
i - to enter insert mode
cw - will delete from cursor to the right and place in insert mode
x - delete character
dd - delete entire line
dG - deletes all lines to the end of file from line the cursor is on
```

## navigation 
```
             ^
             k              Hint:  The h key is at the left and moves left.
       < h       l >               The l key is at the right and moves right.
             j                     The j key looks like a down arrow.
             v
```

## quick navigation:
```
^ or 0 - carret or zero will move cursor to beginning of line
$ - move cursor to end of line
I - move to beginning of line and enter insert mode
A  - move to the end of line and enter insert mode
gg - move to start of file
G - move to end of file

```

## Copying/cutting and pasting: 
```

V - capital V will highlight the current line - You can use arrows to move the cursor down to highligh more lines

	you can use 
	d : to cut highlighted text
	or 
	y : to copy highlighted text

	p : to paste highlighted text

y or d by its self will grab the word the cursor is on 
```

## To search in doc:
```
/"search string"

use: 
  N - to go back an instance
  n - to go to the next instance

```

## To replace string for another:
```
:%s/wordToReplace/replacementWord/gc   - gc will search the whole file and ask for each instance. remove c if you do not want to be prompted
```

## To jump to a given line:
```
:10  - jumps to line 10
```

## if you forgot to sudo into a config file
```
:w !sudo tee %  
```

## to comment out a block of lines 
```
step 1: 'crtl+v' (visual block mode)
step 2: use arrows down(j) and up(k) to select lines
step 3: press - 'I' 
Step 4: type the comment character you want ie #
Step 5: press 'esc'
```

## to uncomment out a block of lines
```
step 1: 'crtl+v' (visual block mode)
step 2: use arrows down(j) and up(k) to select lines
step 3: press 'd'
step 4: press 'esc'
```

## while in insert mode ctrl +n autocompletes based on content in the file
