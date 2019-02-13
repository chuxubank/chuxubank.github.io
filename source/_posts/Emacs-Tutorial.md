---
title: Emacs Tutorial
date: 2019-02-13 09:38:09
tags:
  - Emacs
  - Spacemacs
categories:
  - Editor
toc: true
---
![Spacemacs](http://spacemacs.org/img/screenshots/ss1.png)
<!-- more -->
# Notes on Emacs toturial
## Basic
- M(eta): Option
- s(uper): Command
- S(hift)
- C(ontrol)

### Commands
	C-x C-c	End the Emacs session
	C-g		Quit a partially entered command
	C-x k  	Kill buffer

The following commands are useful for viewing screenfuls:

	C-v	Move forward one screenful
	M-v	Move backward one screenful
	C-l	Clear screen and redisplay all the text, moving the text around the cursor to the center of the screen.

### Cursor control
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

Notice the parallel between `C-f` and `C-b` on the one hand, and `M-f` and `M-b` on the other hand.  Very often Meta characters are used for operations related to the units defined by language (words, sentences, paragraphs), while Control characters operate on basic units that are independent of what you are editing (characters, lines, etc).

This parallel applies between lines and sentences: `C-a` and `C-e` move to the beginning or end of a line, and `M-a` and `M-e` move to the beginning or end of a sentence.

Two other important cursor motion command:

	M-< (META Less-than)   	Moves to the beginning of the whole text
	M-> (META Greater-than)	Moves to the end of the whole text.

Most Emacs commands accept a numeric argument; for most commands, this serves as a repeat-count.  The way you give a command a repeat count is by typing `C-u` and then the digits before you type the command.

> The numeric argument is also called a `prefix argument`, because you type the argument before the command it applies to.

`C-v` and `M-v` are another kind of exception.  When given an argument, they scroll the text up or down by that many lines, rather than by a screenful.  For example, `C-u 8 C-v` scrolls by 8 lines.

### Windows
	C-x 1	One window (i.e., kill all other windows).

There is a whole series of commands that start with `C-x`; many of them have to do with windows, files, buffers, and related things. 
These commands are two, three or four characters long.