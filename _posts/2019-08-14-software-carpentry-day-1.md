---
layout: post
title: Software Carpentry Day 1
description: 
publish: true
categories: 
- misc
---

I attended a Software Carpentry workshop that teaches basic research computing skills. The following useful reference materials are taken from their GitHub pages on [shell scripting]](https://swcarpentry.github.io/shell-novice/reference/), [Python](https://swcarpentry.github.io/python-novice-inflammation/reference/), and [git](https://swcarpentry.github.io/git-novice/reference). These are really useful so I highly recommend using them for basic reference. Advanced version is [here](https://intermediate-and-advanced-software-carpentry.readthedocs.io/en/latest/)

## Bash shell

# Working with files and directories and pipe and filters

* command is a small program that does something (e.g. usage: `command [-flag] [arguments]`)
* 4 types of contents in a directory: directory, file, executable program (\*), symbolic link (@)
* `cat filename` print file content to prompt, can be piped into a text file
* `*` wild card. `[AB]` matches either an ‘A’ or a ‘B’
* `man commandName` to get help for the command (`b` to go up the page, `space` to go down)
* `head -n` prints n lines from the start of a file
* `tail -n` prints n lines from the end of a file
* `cd` to go to home directory, `cd -` to back to the previous directory
* `mv dir1 dir2` moves dir1 and all its files into dir2. Can also move files. No `-r` needed
* `cp -r dir1 dir2` copies dir1 and all its files into dir2
* `rm -ri` remove files. `-i` prompts warning before executing command
* `wc -l/w/m` is the “word count” command: it counts the number of lines (`-l`), words (`-w`), and characters (`-m`) in files (from left to right, in that order)
* `touch` create a generic file (not necessarily a text file) that can be appended to, or can act as notification for job arrays
* `less` displays a screenful of the file. You can go forward one screenful by pressing the `spacebar`, or back one by pressing `b`. Press `q` to quit
* `>` writes text to file, and overwrites the file each time we run the command
* `>>` also writes text to file, but appends the string to the file if it already exists (i.e. when we run it for the second time)
* `|` is called a pipe. It tells the shell that we want to use the output of the command on the left as the input to the command on the right
* “pipes and filters” programming model links programs together. A filter is a program like `wc` or `sort` that transforms a stream of input into a stream of output. Any program that reads lines of text from standard input and writes lines of text to standard output can be combined with every other program that behaves this way as well. You can and should write your programs this way so that you and other people can put those programs into pipes to multiply their power.
* `cut -d , -f 2` removes or “cut out” certain sections of each line in the file. The optional `-d` flag defines the delimiter, or splitting parameter (default is `tab`). `-f` specifies the field (column) to cut out 
* `uniq` filters out **adjacent** matching lines in a file. `-c` flag gives a count of the number of times a line occurs in its input.
* `<` operator redirects input to a command
* shortcut: in command prompt with a long line of words, `opt+arrows` to jump words, `ctrl+a` to go to the beginning, `ctrl+e` to go to the end
* name files or directories from most general to more specific to allow easier search
* `!$` retrieves the last word of the last command
* `ctrl+r` search previous history

# For loops

For loops in shell scripting: 
```
for thing in list_of_things
do
    operation_using $thing    # Indentation within the loop is not required, but aids legibility
done
```
This is useful for going through files and do something with each of them. 
* A loop is a way to do many things at once — or to make many mistakes at once if it does the wrong thing. One way to check what a loop would do is to echo the commands it would run instead of actually running them.
* `echo "do $something"` prints to screen everything enclosed in the quote marks. It redirects the output from the command
* `echo do $something` expands the loop variable name

# Shell scripts

* to make and run a shell script, make `middle.sh`:
```
head -n 15 $1 | tail -n 5
```
then run using 
```
bash middle.sh octane.pdb
```
where `$1` is the first argument (e.g. octane.pdb) from the input.

* To set a variable, do (without space):
```
test_var=20
```
invoke the variable using
```
echo $test_var
```
* `grep expression filename` search for `expression` in `filename`. Lots of options are available for more specific searchf

## Python

# Defensive programming

* Program defensively, i.e., assume that errors are going to arise, and write code to detect them when they do.
* Put assertions in programs to check their state as they run, and to help readers understand how those programs are supposed to work.
* Use preconditions to check that the inputs to a function are safe to use.
* Use postconditions to check that the output from a function is safe to use.
* Write tests before writing code in order to help determine exactly what that code is supposed to do.

* `plt.tight_layout()` removes white space when making figures

* for loops using `enumerate`:
```
for i, character in enumerate(word):
	print(i, character)
```
* lambda
* deep copy
