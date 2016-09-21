---
layout:     post
title:      Use vim to see code
category: blog
description: Some tips to see code using vim
---   

## Open file under cursor    

	gf	open in the same window ("goto file")
	<c-w>f	open in a new window (Ctrl-w f)
	<c-w>gf	open in a new tab (Ctrl-w gf)    
	
If there are several files in your 'path' that match the name under the cursor, gf opens the first, while 2gf opens the second, and 3gf opens the third, etc.  

You can return to the previous buffer using Ctrl-^ or Ctrl-o.   
The reverse of Ctrl-O in Vim is `Ctrl + i or tab`   

## Go to definition using g  

Place the cursor on any variable in your program.
	
	gd will take you to the local declaration.
	gD will take you to the global declaration.
	g* search for the word under the cursor (like *, but g* on 'rain' will find words like 'rainbow').
	g# same as g* but in backward direction.
	gg goes to the first line in the buffer (or provide a count before the command for a specific line).
	G goes to the last line (or provide a count before the command for a specific line).