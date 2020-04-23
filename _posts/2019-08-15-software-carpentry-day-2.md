---
layout: post
title: Software Carpentry Day 2
description: 
published: true
categories: 
- misc
---

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

# Defensive programming

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

# Test-Driven Development

* Steps:
	1. Write a short function for each test.
	2. Write a range_overlap function that should pass those tests.
	3. If range_overlap produces any wrong answers, fix it and re-run the test functions.
* Writing the tests before writing the function they exercise is called test-driven development (TDD)
* `python -i myscript.py` runs the script interactively, then keeps all the variables in memory so you can access them. 

