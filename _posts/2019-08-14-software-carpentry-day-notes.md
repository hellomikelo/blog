---

layout: post
title: Software Carpentry Notes
description: 
published: true
excerpt_separator: <!--more-->
categories: [Miscellaneous]

---

I attended a Software Carpentry workshop that teaches basic research computing skills. The following useful reference materials are taken from their GitHub pages on [shell scripting]](https://swcarpentry.github.io/shell-novice/reference/), [Python](https://swcarpentry.github.io/python-novice-inflammation/reference/), and [git](https://swcarpentry.github.io/git-novice/reference). These are really useful so I highly recommend using them for basic reference. Advanced version is [here](https://intermediate-and-advanced-software-carpentry.readthedocs.io/en/latest/)
<!--more-->

## Bash shell

### Working with files and directories and pipe and filters

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

### For loops

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

### Shell scripts

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

### Defensive programming

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

## Git

* `ctrl+l` clears the terminal screen
* `.gitignore` is a text file that contains the list of all files you don't want git to track changes
* `gif config` to change default preferences
* The idea of adding and committing:
![git](https://swcarpentry.github.io/git-novice/fig/git-staging-area.svg)
* Example workflow:
	1. `git init` # creates an empty .git directory in a new directory to keep track of change history
	2. `git status`
	3. `vi mars.txt`
	4. `git add mars.txt` # gets file changes ready for commit locally
	5. `git commit -m 'change 1'` # adds file to staging area and assign the change an unique ID. You can commit multiple "adds" together (assigned to one ID) to keep track of them all as a single package in the change history.
	6. `vi mars.txt` # makes changes to the working copy of the file
	7. `git diff HEAD~$VERSION_NUM mars.txt` # shows changes between commit and working copy (before `add`). `$VERSION_NUM` is the version number you want to compare the current version to. No `$VERSION_NUM` means most current version
	8. `git commit -m 'change 2'` # add further message 
	9. `git log` # shows history of changes
	10. `git checkout HEAD~$VERSION_NUM mars.txt` # reverses change (but does not delete new changes), i.e. replaces the working copy with the most recently committed version. `$VERSION_NUM` is the version number you want to revert to
	11. `git stash` # put all uncommitted changes to "stash" directory
	12. `git revert` # ? Deletes files when reverting commit?
	13. `git pull origin master` # pull changes from remote repo (origin)into local machine (master)
	14. `git remote add origin git@github.com:...` # link local repo to remote repo
	15. `git push -u origin master` # push changes from local repo to remote repo

## Python 

* To install new [extensions](https://github.com/ipython-contrib/jupyter_contrib_nbextensions) in jupyter notebook
* `glob` finds files and directories whose names match a pattern

### Defensive programming

Make programs assuming that mistakes will happen and to guard against them.
* An assertion is simply a statement that checks something to be true at a certain point in a program. It also helps people understand programs. Each assertion gives the person reading the program a chance to check (consciously or otherwise) that their understanding matches what the code is doing.
* Most good programmers follow two rules when adding assertions to their code. 
	1. **Fail early, fail often.** The greater the distance between when and where an error occurs and when it’s noticed, the harder the error will be to debug, so good code catches mistakes as early as possible.
	2. **Turn bugs into assertions or tests.** Whenever you fix a bug, write an assertion that catches the mistake should you make it again. If you made a mistake in a piece of code, the odds are good that you have made other mistakes nearby, or will make the same mistake (or a related one) the next time you change it. Writing assertions to check that you haven’t regressed (i.e., haven’t re-introduced an old problem) can save a lot of time in the long run, and helps to warn people who are reading the code (including your future self) that this bit is tricky.
* Three main types: 
	1. A **precondition** is something that must be true at the start of a function in order for it to work correctly
	2. A **postcondition** is something that the function guarantees is true when it finishes
	3. An **invariant** is something that is always true at a particular point inside a piece of code
* e.g. 
```
assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
```
* print progress of program often to keep track of potential errors, and to inform about its status
* print errors with as much relevant information as possible

### Test-Driven Development

* Steps:
	1. Write a short function for each test.
	2. Write a range_overlap function that should pass those tests.
	3. If range_overlap produces any wrong answers, fix it and re-run the test functions.
* Writing the tests before writing the function they exercise is called test-driven development (TDD)
* `python -i myscript.py` runs the script interactively, then keeps all the variables in memory so you can access them. 
