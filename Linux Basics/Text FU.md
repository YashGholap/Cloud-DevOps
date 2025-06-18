---
tags: [Linux]
title: Text FU
created: '2025-06-14T06:19:22.678Z'
modified: '2025-06-14T18:43:53.696Z'
---

# Text FU
---
1. stdout (Standard Output) - >
  - It allows us to send the output of echo Hello World to a file instead of the screen. If the file does not already exist it will create it for us. However, if it does exist it will overwrite it (you can add a shell flag to prevent this depending on what shell you are using).
  eg. 
    ```
    $ echo hello world > new_file.txt
    ```

  - Well let's say I didn't want to overwrite my peanuts.txt, luckily there is a redirection operator for that as well, `>>`
  eg.
    ```
    $ echo some test text >> new_file.txt
    ```

2. stdin (Standard Input) - < 
  - 
  ```
  $ cat < peanuts.txt > banana.txt
  ```
  Just like we had > for stdout redirection, we can use < for stdin redirection.
  - Normally in the cat command, you send a file to it and that file becomes the stdin, in this case, we redirected peanuts.txt to be our stdin. Then the output of cat peanuts.txt which would be Hello World gets redirected to another file called banana.txt.

3. stderr (Standard Error) - 2>
  - There is actually another I/O stream in play here called standard error (stderr). By default, stderr sends its output to the screen as well, it's a completely different stream than stdout.
  - We will have to use file descriptors. A file descriptor is a non-negative number that is used to access a file or stream. know that the file descriptor for stdin, stdout and stderr is 0, 1, and 2 respectively.
  - eg.
    ```
    $ ls /fake/directory 2> peanuts.txt
    ```
  - Now what if I wanted to see both stderr and stdout in the peanuts.txt file? It's possible to do this with file descriptors as well:
  ```
  $ ls /fake/directory > peanuts.txt 2>&1
  ```
  shorter way
  ```
  $ ls /fake/directory &> peanuts.txt
  ```
  - Now what if I don't want any of that cruft and want to get rid of stderr messages completely? Well you can also redirect output to a special file call /dev/null and it will discard any input.
  ```
  $ ls /fake/directory 2> /dev/null
  ```

4. pipe and tee
  - Instead of redirecting this output to a file, wouldn't it be nice if we could just see the output in another command like less? Well we can!
  ```
  $ ls -la /etc | less
  ```
  - The pipe operator |, represented by a vertical bar, allows us to get the stdout of a command and make that the stdin to another process. In this case, we took the stdout of ls -la /etc and then piped it to the less command.
  - Well what if I wanted to write the output of my command to two different streams? That's possible with the tee command:
  ```
  $ ls | tee peanuts.txt
  ```

5. env
  - 
    ```
    $ echo $HOME
    ```  
    You should see the path to your home directory.
  -
    ```
    $ env
    ```
    This outputs a whole lot of information about the environment variables you currently have set. These variables contain useful information that the shell and other processes can use.
  - You can access these variables by sticking a $ infront of the variable name

6. cut 
  - first let's and text in file also adding an tab into the space.
  ```
  $ echo -e "The quick brown; fox jumps over the lazy\tdog" > sample.txt
  ```
  - `cut` command extracts portions of text from a file.
  To extract contents by a list of characters:
  ```
  cut -c 5 sample.txt
  ```
  This outputs the 5th character in each line of the file. In this case it is "q", note that the space also counts as a character.
  - To extract the contents by a field, we'll need to do a little modification:
    ```
    $ cut -f 2 sample.txt
    ```
    The -f or field flag cuts text based off of fields, by default it uses TABs as delimiters, so everything separated by a TAB is considered a field. You should see "dog" as your output.
  - You can combine the field flag with the delimiter flag to extract the contents by a custom delimiter:
    ```
    $ cut -f 1 -d ";" sample.txt
    ```
  - we can also do:
    - `cut -c 5-10 sample.txt` : this will return the characters from 5 to 10 ie *quick* in this case.
    - `cut -c 5- sample.txt` : this will return everything after the 5th character including the 5th number ie *quick brown; fox jumps over the lazy    dog* in our case.
    - `cut -c -5 sample.txt` : this opposite of `5-` it will return everything before 5th character. ie *The q* in our case.

7. Paste
  - The paste command is similar to the cat command, it merges lines together in a file.
  - Suppose a file named sample2.txt and has contents:
  ```
  The
  quick
  brown
  fox
  ```
  now to combine all these into one line we can use:
  ```
  $ paste -s (s for --serial) sample2.txt
  ```
  This will give: `The     quick   brown   fox`

  - The default delimiter for paste is TAB, so now there is one line with TABs separating each word.
 Let's change this delimiter (-d) to something a little more readable:
 ```
 $ paste -d ' ' -s sample2.txt
 ```
 This will give : `The quick brown fox`

8. head
  - the head command will show you the first 10 lines in a file. (default)
  ```
  $ head /var/log/syslog
  ```
  - You can also modify the line count to whatever you choose. To do that we need to use the `-n` (n for number of lines).
  ```
  $ head -n 15 /var/log/syslog
  ```

9. tail
  - same as head but shows last 10 lines by default.
  - we can also specify the number of lines we want to view from last in the same manner as head using `-n` flag.
  - There is `-f` (f for follow) which is extra feature in tail. where we can follow the file as it changes.

10. join & split
  - The join command allows you to join multiple files together by a common field.
  ```
  $ join file1.txt file2.txt
  ```
  - They are joined together by the first field by default and the fields have to be identical, if they are not you can sort them.
  - Suppose we want field 2 on file1.txt and field 1 on file2.txt, so the command would look like this:
  ```
  join -1 2 -2 2 file1.txt file2.txt 
  ```
  Here `-1` refers to file1.txt and `-2` refers to file2.txt.
  - You can also split a file up into different files with the split command.
  ```
  $ split file1.txt
  ```
  This will split it into different files, by default it will split them once they reach a 1000 line limit. The files are named x** by default.

11. sort
  - Used to sort the content of a file alphabetically.
  - `-r` flag can be used to reverse sort the content.
  - `-n` flag can be used to sort it numerically (file should contain numbers).

12. uniq
  - Used to remove the duplicates.
  - `-c` flag is used to count the number of occurences of a line.
  - `-u` flag is used to get just the unique value.
  - `-d` flag is used to get just the duplicate values.
  *Note : uniq does not detect duplicate lines unless they are adjacent.*
  - To overcome this limitation of uniq we can use sort in combination with uniq:
  ```
  $ sort reading.txt | uniq
  ```
13. grep
  - It allows you to search files for characters that match a certain pattern.
  ```
  $ grep fox sample.txt
  ```
  - `-i` flag can be used to grep patterns that are case insensitive.
  - You can even use regular expressions in your pattern:
  ```
  $ ls /somedir | grep '.txt$'
  ```

  



  
