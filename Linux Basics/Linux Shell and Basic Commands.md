---
tags: [Linux]
title: Linux Shell and Basic Commands
created: '2025-06-12T16:57:48.616Z'
modified: '2025-06-13T16:55:54.289Z'
---

# Linux Shell and Basic Commands
---
## Command Line
1. echo ....
  - eg echo hello world
  - prints ` hello world ` on console

2. date
  - date gives date in UTC format  - ` Thu Jun 12 16:20:42 UTC 2025 `

3. Whoami
  - prints the name of the user.

4. pwd (print working directory)
  - gives address of where we are in folder structure with context of root.

5. cd (change directory)
  - Path :
    - absolute path : This is the path from the root directory, starts with `/`, eg `/home/yash`.
    - relative path : his is the path from where you are currently in filesystem.
  - `cd .` - change to current directory.
  - `cd ..` - change to parent directory or one level up.
  - `cd ~` - change the directory to *Home Directory*.
  - `cd -` - change to previous path or directory *(can be used to toggle)*.

6. ls (list directories)
  - list directories and files in the current directory by default,however you can specify which path you want to list the directories of. eg 
  ```
  ls /home/yash
  ```

  - flags:
    - `-a` : a for all. Shows all the files including hidden folders.
    - `-l` : l for long. This will show you detailed information, starting from the left: file permissions, number of links, owner name, owner group, file size, timestamp of last modification, and file/directory name.
    - `-la` : this will merge both the flags work and give result.
    - `-R` : recursively list directory contents.
    - `-r` : reverse order while sorting.
    - `-t` : sort by modification time, newest first.

7. touch 
  - Touch allows you to the create new empty files.
  - Touch is also used to change timestamps on existing files and directories.

8. file
  - To find out what kind of file a file is, you can use the file command. It will show you a description of the file’s contents.

9. cat (concatenate)
  - it not only displays file contents but it can combine multiple files and show you the output of them.
  - it’s only meant for short content.

10. less
  - The text is displayed in a paged manner, so you can navigate through a text file page by page.
  - Use the following command to navigate through less:
    - q - Used to quit out of less and go back to your shell.
    - Page up, Page down, Up and Down - Navigate using the arrow keys and page keys.
    - g - Moves to beginning of the text file.
    - G - Moves to the end of the text file.
    - /search - You can search for specific text inside the text document. Prefacing the words you want to search with /
    - h - If you need a little help about how to use less while you’re in less, use help.

    *All this commands is valid inside less.*

11. history
  - displays all the command history ie commands we used earlier.
  - `ctrl + R` : This helps to find the command by searching it in the history suggest previously command.

12. cp
  - Much like copy and pasting files in other operating systems, the shell gives us an even simpler way of doing that.
  ```
  cp mycoolfile /home/pete/Documents/cooldocs
  ```
  - You can use wildcards in every command for more flexibility.
    - ` *` the wildcard of wildcards, it's used to represent all single characters or any string.
    - `?` used to represent one character
    - `[]` used to represent any character within the brackets
    ```
    $ cp *.jpg /home/pete/Pictures
    ```
  - flags:
    - `-r` : this will recursively copy the files and directories within a directory.
    - `-i` : You can use the -i flag (interactive) to prompt you before overwriting a file.
  
13. mv
  - Used for moving files and also renaming them. Quite similar to the cp command in terms of flags and functionality.
  - You can rename files like this:
    ``` 
    $ mv oldfile newfile 
    ```
  - Or you can actually move a file to a different directory:
    ```
    $ mv file2 /home/pete/Documents
    ```
  - And move more than one file:
    ```
    $ mv file_1 file_2 /somedirectory
    ```
  - You can rename directories as well:
    ```
    $ mv directory1 directory2
    ```

  - Like cp, if you mv a file or directory it will overwrite anything in the same directory. So you can use the -i flag to prompt you before overwriting anything.
    ```
    mv -i directory1 directory2\
    ```
  - Let’s say you did want to mv a file to overwrite the previous one. You can also make a backup of that file and it will just rename the old version with a ~.
    ```
    $ mv -b directory1 directory2
    ```
14. mkdir
  - t will create a directory if it doesn’t already exist.
  - You can even make multiple directories at the same time.
    ```
    $ mkdir books paintings
    ```
  - You can also create subdirectories at the same time with the -p (parent flag).
    ```
    $ mkdir -p books/hemmingway/favorites
    ```
15. rm 
  - To remove files you can use the rm command.
  - flags : 
    - `-f` : -f or force option tells rm to remove all files, whether they are write protected or not, without prompting the user (as long as you have the appropriate permissions).
    - `-i` : will give you a prompt on whether you want to actually remove the files or directories.
    - `-r` : -r flag (recursive) to remove all the files and any subdirectories it may have.
16. find
  - finds the file, folder or anything that we want to search from.With find you’ll have to specify the directory you’ll be searching it, what you’re searching for, in this case we are trying to find a file by the name of puppies.jpg.
  ```
  $ find /home -name puppies.jpg
  ```
  - You can see that I set the type of file I’m trying to find as (d) for directory and I’m still searching by the name of MyFolder.
  ```
  $ find /home -type d -name MyFolder
  ```
17. man
  - you can see the manuals for a command with the man command.
  eg. 
    ```
      $ man ls
    ```
18. whatis
  - he whatis command provides a brief description of command line programs.
  eg.
    ```
    $ whatis cat
    ```
19.alias
  - If you need to type a long command many times, it’s best to have an alias you can use for that.
  - To create an alias for a command you simply specify an alias name and set it to the command.
    ```
    $ alias foobar='ls -la'
    ```
  - You can remove aliases with the unalias command:
    ```
    $ unalias foobar  
    ```

---
## Resources
- [Linux Fundamentals Course](https://linuxjourney.com/)
- [WSL](https://youtu.be/wz0QBNy9i7w?si=0pO8YLjzqsuiQocX)
