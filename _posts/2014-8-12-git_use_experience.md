---
layout: post
title: gitstudy
excerpt: "help learn git command"
tags: [others]
comments: true
---


###git use experience
standard workflow
	
	modified ==> add ==> commit ==> push

undoing local changes(before staging)

	git checkout <filename> # return to the state of last commit
	
undoing staged changes(before committing)

	git reset HEAD <filename> # get to the state of the above code
	
removing commits from a branch

	git reset —hard v1／hashcode # revert to certain version code 
	
move file

	git mv oldname newname
	
	equals to
	
	mv oldname newname
	git add newname
	git rm oldname
	

getting old version

	git hist
	git checkout/co <hash>
	git checkout master # get to the lastest state of the branck master(default branch)

tagging versions

	git tag v1 # tag the current version v1
	git checkout v1^ # get to the parent version of v1
	
create a branch

	git checkout -b <branchname>

switch between branches

	git checkout <branchname>
	
merge the branches

	git checkout greet # destination
	git merge master # branch to be merged from
		
rebasing, another way for merging (leave a linear and much easier to read chain of commits), but should be __carefull to use it for it rewriting the commit history__

	git co greet
	git rebase master 

get repository

	git clone <address>
	
fetching changes from remote repository and combine them to the repository

	git fetch
	git merge origin/master
	
	equals to
	
	git pull
	
add a local branch that tracks a remote branch

	git branch —track localname origin/remotename
	git branch -a
	
bare repository (repository without working directories)

	git clone —bare source reponame barereponame.git

pushing a change to a remote repository

	do the correct
	git checkout master
	git add filename
	git commit …
	git push shared master

adding a remote repository

	git remote add shared remoterepoaddress
	
pulling shared changes

	git remote add shared remoterepoaddress
	git branch —track shared master
	git pull shared master

#### difference between git reset and revert
	
	git reset destifilename # like not exist startpoint
	git revert HEAD #create another could share the reversed changes twith other

#### when git push, prompt fatal: Reference has invalid format: 'refs/heads/master (linux's conflicted copy 2014...)

- solution

		cd repository
		find . -type f -name "* conflicted copy*" -exec rm -f {} \;
		awk '!/conflicted/' .git/packed-refs > temp && mv temp .git/packed-refs


	git init # create a .git/ directory to save all the information about the stuff
	git status # 
	main branch # master branch
	
	. . . . . #main branch (master)
		.
		 . . .#used to test other functions
		 
	git add ./file_name
	git commit -m(means add a message) "content"
	git log # see the structure
		commit unique codels
		
	git checkout hash_number # go back to an old version, be careful
	
	remote location nickname always be origin
	git pull origin master # pull from remote origin to my computer
	git push
	git remote -v # to see the remote repositories name
	