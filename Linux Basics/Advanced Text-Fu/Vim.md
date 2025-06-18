---
tags:
  - Advanced_Text-Fu
title: Vim
---
- To use vim we need to pass the file as argument.
```
vim sample.txt
```
- This will open a new file named `sample.txt` (or open it if it already exists).
- You are now in **Normal Mode**. You'll see a blank screen or the content of `sample.txt`.
1. Entering and Exiting Insert Mode (Typing Text):
	-  To enter Insert Mode:
		- press `i` key (i for "insert"). You'll likely see `-- Insert --` at the bottom of your terminal screen.
		- Now you can type whatever you want, just like a regular editor.
	- To exit Insert Mode and go back to Normal Mode:
		- Press the `Esc` key. The `-- INSERT --` indicator at the bottom should disappear.
		- **This is crucial!** Always return to Normal Mode after typing.
2. Saving and Quitting:
	- **You must be in Normal Mode to do this!** (Press `Esc` if you're in Insert Mode).
	- To save the file:
		- Type `:w` (colon followed by 'w' for "write"). Press Enter.
		- You'll see a message like `"sample.txt" [New] 3L, 45B written` at the bottom.
	- To quit Vim:
		- Type `:q` (colon followed by 'q' for "quit"). Press Enter.
		- If you haven't saved your changes, Vim will warn you. To quit without saving, type `:q!` and press Enter.
		- To save an quit at the same time. Type `:wq` (write and quit). Press Enter.
3. Searching: 
	- To search for an expression:
		- Type the `/` key and then your search result while you are in a vim session. Press Enter.
		- The ? search command will search the text file backwards, so in the previous example, the last pretty would come up first.
```
		/pretty
		?pretty
``` 
		



