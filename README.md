# Git commands Documentation for your reference
***
* Git works on concept of Source Code Management (SCM) \
* It is called Distributed Version Control System \
* Trunk Based Development : supports branching \
***

### --To setup configurations:
$ git config --global user.name Shivanshi23
<br/>
$ git config --global user.email shivanshigarg2303@gmail.com
<br/>
$ git config --global user.name <br/>
Shivanshi23
<br/>
$ git config --global user.email <br/>
shivanshigarg2303@gmail.com
<br/>
### --To clear the screen
$ clear
<br/>
### --To create empty git repository
$ git init <br/>

<br/>
### --To see hidden folders 
$ ls -lart <br/>
total 4 <br/>
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 21:58 ../ <br/>
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 22:00 ./ <br/>
drwxr-xr-x 1 Shivanshi Garg 197609 0 May 23 22:00 .git/ <br/>
<br/>
### --To know status of files
$ git status <br/>
//UNTRACKED files : files not tracked by git. <br/>
//STAGED files : When we add a file, it reside in Staging area, got tracked and are ready to commit. <br/>
//UNMODIFIED files : If we commit any tracked file, it goes to unmodified category. <br/>
//MODIFIED files : if we edit the file, then it goes to modified category. Then, we stage the file, so that changes can be committed from there.<br/>
<br/>
### --To open visual code
$ code .
<br/>
### --To create empty files in VS code
$ touch about.html
<br/>
$ touch news.html
<br/>
$ git status 
<br/>
//As of now, these are untracked files
<br/>

### Step 1: To add the file (Staged)
//to add files in Staging area(if we want the files to be tracked by git)<br/>
$ git status

<br/>
//Now, only about.html file is STAGED and news.html is still UNTRACKED.
<br/>
### --To ADD all files of current folder into STAGING area
$ git add -A
<br/>
//Now, all files are STAGED but commit is not done
<br/>
### Step 2: To commit a file (UNMODIFIED)
$ git commit -m "first commit"
<br/>
### --To match a file with last commit
e.g. if someone deleted my about.html content, then we can get the last committed content.<br/>
$ git checkout about.html
<br/>
### --To match all files with last commit
$ git checkout -f
<br/>
### --To list all commits made by me
$ git log
<br/>
### --To get last few commits (mention number for how many commit's info you require from last)<br/>
$ git log -p -1 //or git log -p -2
<br/>
$ touch contact.html
<br/>
### Step 3 : Edit news.html (UNMODIFIED -> MODIFIED)
<br/>
### STEP 4 : MODIFIED -> STAGED
//if we modify a file, we need to again add it to STAGING area
e.g. we made changes to news.html<br/>
$ git add -A
<br/>
$ git status<br/>
On branch master<br/>
Changes to be committed:<br/>
  (use "git reset HEAD <file>..." to unstage)<br/>
<br/>
        new file:   contact.html
        modified:   news.html
<br/>
<br/>
//git is making track of all files
<br/>
### file shown in red color in $ git status, is UNSTAGED
### file shown in green color in $ git status, is STAGED
<br/>
//Edit all files (MODIFIED)<br/>
//Now, either STAGE the files or direct COMMIT
<br/>
### --Skipping the STAGED area (direct COMMIT all files without going to STAGING area)
MODIFIED -> UNMODIFIED (COMMIT) <br/>
$ git commit -a -m "Skipping the STAGED area"
<br/>
### --To list all files in current folder
$ ls<br/>
about.html  contact.html  news.html
<br/>
### --To show present working directory
$ pwd<br/>
/e/Samsung/All about git
<br/>
### --To remove file from STAGING area
$ git rm --cached delete.html<br/>
rm 'delete.html'
<br/>
### --To deleted commited file
$ git rm delete.html
<br/>
//if we won't commit the changes, then we can get back the deleted file from $ git checkout -f(by matching files with last commit)
<br/>
$ git rm --cached delete.html<br/>
It will delete the file but changes are not commited.<br/>
Also, "--cached" adds the file to untracked files. We can still retrieve the file by adding it.<br/>
<br/>
### --For force removal of file
$ git rm -f delete.html
<br/>
### --shorthand command for git status
$ git status -s
<br/>
### --To add .gitignore file (it has info of the files to be ignored)
$ touch .gitignore<br/>
If we want that git does not track or commit some set of files, we write those file names in .gitignore file
<br/>
e.g. create mylogs.log file and write its name in .gitignore file<br/>
Now, if we see status, mylogs.log file is not tracked
<br/>
$ git add -A <br/>
//to track .gitignore file
<br/>
Create mylogs folder, then add mylogs.log file in it.<br/>
It also get ignored because file name written in .gitignore
if we want mylogs folder to be ignored only, then write /mylogs in .gitignore<br/>
<br/>
$ git add -A<br/>
$ git commit -m "Adding git ignore  file"<br/>
//commit all changes till now<br/>
<br/>
## Branching
<br/>
### --To check the list of branches available in project
$ git branch
* master
<br/>
### --To create new branch
$ git branch updatecode
<br/>
$ git branch
* master<br/>
  updatecode<br/>
//Now we have two branches : master, updatecode<br/>
<br/>
### --Switch to other branch
$ git checkout updatecode<br/>
Switched to branch 'updatecode'
<br/>
//made some changes to about, news file. added new file comment.html
<br/>
$ git add -A
<br/>
//now check status<br/>
//need to commit changes(direct commit skipping staging)<br/>
<br/>
$ git commit -a -m "Update code"
<br/>
//we can see that comment.html file is only present in "updatecode" branch and not in master branch.
<br/>
### --To merge any branch to master branch
first, switch to master branch
<br/>
$ git checkout master
<br/>
$ git merge updatecode
<br/>
<br/>
//Let's create node files for back-end
<br/>
### --To create new branch and switch to it simultaneously
$ git checkout -b nodeintegration<br/>
Switched to a new branch 'nodeintegration'
<br/>
$ git touch node.js
<br/>
$ git add -A
<br/>
$ git commit -m "server side js file"
<br/>
## Current status :
-update code branch merged with master branch<br/>
-nodeintegration branch is separate as of now<br/>
-let's push master branch code to github account<br/>
//for this create empty repo on github "Git commands Demo"<br/>
<br/>
### --To push master branch to github account(remote got repo)
$ git remote add origin https://github.com/Shivanshi23/Git-commands-Demo.git
<br/>
$ git push origin master
<br/>
## For explanation
--To push local branch to remote git repo
1. Create new branch.<br/>
$ git checkout -b new_branch<br/>
2. Edit, add and commit your files.<br/>
3. Push your branch to the remote repository<br/>
$ git push origin new_branch
<br/>
### --Adding local branch to remote server
$ git push origin nodeintegration
<br/>
### --To clone a project into local system
//goto the directory in which u want to clone the project<br/>
$ git clone https://github.com/Shivanshi23/Git-commands-Demo.git folder_name <br/>
// repository URL : url of git project<br/>
// folder_name : the folder in which you want to copy the project<br/>
<br/>
### --To pull a repository
$ git pull <option> https://github.com/Shivanshi23/Git-commands-Demo.git <br/>
//The term pull is used to receive data from GitHub. <br/>
It fetches and merges changes from the remote server to your working directory. <br/>
The git pull command is used to pull a repository.<br/>
<br/>























