# Git commands Documentation for your reference
***
--Git works on concept of Source Code Management (SCM)
--It is called Distributed Version Control System
--Trunk Based Development : supports branching
***

### --To setup configurations:
$ git config --global user.name Shivanshi23
---
$ git config --global user.email shivanshigarg2303@gmail.com
---
$ git config --global user.name
Shivanshi23
---
$ git config --global user.email
shivanshigarg2303@gmail.com
---
### --To clear the screen
$ clear
---
### --To create empty git repository
$ git init
Initialized empty Git repository in E:/Samsung/All about git/.git/
---
### --To see hidden folders 
$ ls -lart
total 4
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 21:58 ../
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 22:00 ./
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 22:00 .git/
---
### --To know status of files
$ git status
//UNTRACKED files : files not tracked by git.
//STAGED files : When we add a file, it reside in Staging area, got tracked and are ready to commit.
//UNMODIFIED files : If we commit any tracked file, it goes to unmodified category.
//MODIFIED files : if we edit the file, then it goes to modified category. Then, we stage the file, so that changes can be committed from there.
---
### --To open visual code
$ code .
---
### --To create empty files in VS code
$ touch about.html
---
$ touch news.html
---
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        about.html
        news.html

nothing added to commit but untracked files present (use "git add" to track)
---
//As of now, these are untracked files
---
### --Step 1: To add the file (Staged)
//to add files in Staging area(if we want the files to be tracked by git)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   about.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        news.html

---
//As of now, only about.html file is STAGED and news.html is still UNTRACKED.
---
### --To ADD all files of current folder into STAGING area
$ git add -A
---
//Now, all files are STAGED but commit is not done
---
### --Step 2: To commit a file (UNMODIFIED)
$ git commit -m "first commit"
---
### --To match a file with last commit
--e.g. if someone deleted my about.html content, then we can get the last committed content.
$ git checkout about.html
---
### --To match all files with last commit
$ git checkout -f
---
### --To list all commits made by me
$ git log
---
### --To get last few commits (mention number for how many commit's info you require from last)
$ git log -p -1 //or git log -p -2
---
$ touch contact.html
---
### --Step 3 : Edit news.html (UNMODIFIED -> MODIFIED)
---
### --STEP 4 : MODIFIED -> STAGED
//if we modify a file, we need to again add it to STAGING area
e.g. we made changes to news.html
$ git add -A
---
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   contact.html
        modified:   news.html

---
//git is making track of all files
---
## file shown in red color in $ git status, is UNSTAGED
## file shown in green color in $ git status, is STAGED
---
//Edit all files (MODIFIED)
//Now, either STAGE the files or direct COMMIT
---
### --Skipping the STAGED area (direct COMMIT all files without going to STAGING area)
// MODIFIED -> UNMODIFIED (COMMIT)
$ git commit -a -m "Skipping the STAGED area"
---
### --To list all files in current folder
$ ls
about.html  contact.html  news.html
---
### --To show present working directory
$ pwd
/e/Samsung/All about git
---
### --To remove file from STAGING area
$ git rm --cached delete.html
rm 'delete.html'
---
### --To deleted commited file
$ git rm delete.html
---
//if we won't commit the changes, then we can get back the deleted file from $ git checkout -f(by matching files with last commit)
---
$ git rm --cached delete.html
//it will delete the file but changes are not commited.
//Also, "--cached" adds the file to untracked files. We can still retrieve the file by adding it
---
### --For force removal of file
$ git rm -f delete.html
---
### --shorthand command for git status
$ git status -s
---
### --To add .gitignore file (it has info of the files to be ignored)
$ touch .gitignore
//if we want that git does not track or commit some set of files, we write those file names in .gitignore file
---
e.g. create mylogs.log file and write its name in .gitignore file
Now, if we see status, mylogs.log file is not tracked
---
$ git add -A 
//to track .gitignore file
---
//create mylogs folder, then add mylogs.log file in it.
It also get ignored because file name written in .gitignore
if we want mylogs folder to be ignored only, then write /mylogs in .gitignore
---
$ git add -A
$ git commit -m "Adding git ignore  file"
//commit all changes till now
---
## Branching
---
### --To check the list of branches available in project
$ git branch
* master
---
### --To create new branch
$ git branch updatecode
---
$ git branch
* master
  updatecode
//Now we have two branches : master, updatecode
---
### --Switch to other branch
$ git checkout updatecode
Switched to branch 'updatecode'
---
//made some changes to about, news file. added new file comment.html
---
$ git add -A
---
//now check status
//need to commit changes(direct commit skipping staging)
---
$ git commit -a -m "Update code"
---
//we can see that comment.html file is only present in "updatecode" branch and not in master branch.
---
### --To merge any branch to master branch
//first, switch to master branch
---
$ git checkout master
---
$ git merge updatecode\
---
---
//Let's create node files for back-end
---
### --To create new branch and switch to it simultaneously
$ git checkout -b nodeintegration
Switched to a new branch 'nodeintegration'
---
$ git touch node.js
---
$ git add -A
---
$ git commit -m "server side js file"
---
## Current status :
-update code branch merged with master branch
-nodeintegration branch is separate as of now
-let's push master branch code to github account
//for this create empty repo on github "Git commands Demo"
---
### --To push master branch to github account(remote got repo)
$ git remote add origin https://github.com/Shivanshi23/Git-commands-Demo.git
---
$ git push origin master
---
## For explanation
--To push local branch to remote git repo
1. Create new branch.
$ git checkout -b new_branch
2. Edit, add and commit your files.
3. Push your branch to the remote repository
$ git push origin new_branch
---
### --Adding local branch to remote server
$ git push origin nodeintegration
---
### --To clone a project into local system
//goto the directory in which u want to clone the project
$ git clone <repository URL> <folder_name>
// repository URL : url of git project
// folder_name : the folder in which you want to copy the project
---
### --To pull a repository
$ git pull <option> <repository URL>
//The term pull is used to receive data from GitHub. 
It fetches and merges changes from the remote server to your working directory. 
The git pull command is used to pull a repository.
---























