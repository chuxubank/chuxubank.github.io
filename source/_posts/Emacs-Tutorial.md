---
title: Emacs Tutorial
date: 2019-02-13 09:38:09
categories:
  - Editor
tags:
  - Emacs
toc: true
---
![Spacemacs](http://spacemacs.org/img/screenshots/ss1.png)
<!-- more -->
# Basic
	M	Meta (Option)
	s	Super (Command)
	S	Shift
	C	Control

# Summary
	C-x C-c End the Emacs session
	C-g     Quit a partially entered command
	C-x k   Kill buffer

	C-v     Move forward one screenful
	M-v     Move backward one screenful
	C-l     Clear screen and redisplay all the text, moving the text around the cursor to the center of the screen.

# Basic cursor control
	C-f	Move forward a character
	C-b	Move backward a character

	M-f	Move forward a word
	M-b	Move backward a word

	C-n	Move to next line
	C-p	Move to previous line

	C-a	Move to beginning of line
	C-e	Move to end of line

	M-a	Move back to beginning of sentence
	M-e	Move forward to end of sentence

	M-< (META Less-than)    Moves to the beginning of the whole text
	M-> (META Greater-than) Moves to the end of the whole text.

Most Emacs commands accept a numeric argument; for most commands, this serves as a repeat-count.  The way you give a command a repeat count is by typing `C-u` and then the digits before you type the command.

> The numeric argument is also called a `prefix argument`, because you type the argument before the command it applies to.

`C-v` and `M-v` are another kind of exception.  When given an argument, they scroll the text up or down by that many lines, rather than by a screenful.  For example, `C-u 8 C-v` scrolls by 8 lines.

# Windows
	C-x 1	One window (i.e., kill all other windows).

There is a whole series of commands that start with `C-x`; many of them have to do with windows, files, buffers, and related things. 
These commands are two, three or four characters long.

# Inserting and deleting
`electric`: when you start typing on the newly created line, the text lines up with that on the previous line.

	<DEL>   Delete the character just before the cursor
	C-d     Delete the next character after the cursor

	M-<DEL> Kill the word immediately before the cursor
	M-d     Kill the next word after the cursor

	C-k     Kill from the cursor position to end of line
	M-k     Kill to the end of the current sentence
	
	C-<SPC> Set mark
	C-w     Kill all the text between two mark positions.

	C-y     Yank the killed text.
	M-y     Replaces that yanked text with the previous kill.

The difference between "killing" and "deleting" is that "killed" text can be reinserted (at any position), whereas "deleted" things cannot be reinserted in this way (you can, however, undo a deletion--see below).
Reinsertion of killed text is called "yanking". (Think of it as yanking back, or pulling back, some text that was taken away.)
Generally, the commands that can remove a lot of text kill the text (they are set up so that you can yank the text), while the commands that remove just one character, or only remove blank lines and spaces, do deletion (so you cannot yank that text). `<DEL>` and `C-d` do deletion in the simplest case, with no argument. When given an argument, they kill instead.

# Undo
	C-/    Undo
	C-_    Undo
	C-x u  Undo

# Files
	C-x C-f    Find a file
	C-x C-s    Save the file

# Buffers
	C-x C-b   List buffers
	C-x b     Go to a buffer
	C-x s     Save some buffers

# Extending the command set
	C-x    Character eXtend. Followed by one character.
	M-x    Named command eXtend. Followed by a long name.
	C-z    "suspends" Emacs

# Auto save
	M-x recover-this-file    Recover the auto-save data

# Mode line
	M-x text-mode    A major mode for editing human-language text
	
	C-h m    View documentation on your current major mode
	
	M-x auto-fill-mode    Breaks the line
	C-x f                 Set the margin
	M-q                   Re-fill the paragraph

# Searching
	C-s	Forward search
	C-r	Reverse search

# Mutiple windows
	C-x 2	Split the screen into 2 windows
	C-M-v	Scroll the "other" window
	C-x o	Move the cursor to the "other" window
	
	C-x 4 C-f	find-file-other-window

# Mutiple frames
	C-x 5 2	New frame (s-n)
	C-x 5 0	Remove the selected frame (s-w)

# Recursive editing levels
	<ESC> <ESC> <ESC>	Get out of recursive editing level

# Getting more help
	C-h	The Help character
	C-h c	The most basic HELP feature
	C-h k	Display the documentation of the function
	C-h f	Describe a function
	C-h v	Display the documentation of variables
	C-h a	Command Apropos
	C-h i	Read included Manuals (a.k.a. Info)