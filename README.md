### Git commands

* git clone "repo URL"
    - this will clone a remote repo to local system
* git status 
    - it will show the files in staging area and files not yet added to staging area. 
* git add "filename"
    - this will add the files to staging area in local system
* git commit -m "commit message"
    - this will commit the changes to local repo
* git log
    - this will show last few actions performed (commits and reverts) with their IDs


* git push
    - it will push the local repo files (which are committed) to remote repo

### Reverting
```
to revert a change we need the id of that change (commit id)
to get this ==> use  git log 
copy the id which we need to revert
then run the following command 

```
1. git log
2. copy the log id
3. git revert "log id"
4. bash editor will be opened, in command mode enter   :q to complete the action.

above process will directly revert and commit the changes to local repo.
but if we want to first revert the files and then explicitly commit then try following command.

* git revert -n "log id"

* git commit -m "commit message"

### Undoing
```
To get back to a particular state such we need to undo all changes we made after that state.
ex :
log : 
4 ----
3 ----
2 ----
1 ----
if we want to go back to log 2 and undo the actions 3 and 4 then we have to use reset command.

```
1. copy the commit id in log  to where we want to go back.
2. git reset --hard "commit id"

### Branches in Git
```
If we want change our code for some temporary session. we may not sure about what will happen after the changes
in such case we dont want to chage the previous code. we just copy it somewhere and apply changes to it.
instead we can do branching to achieve this.
by default git provides master brabch.
if we want to make changes without changing the original code then we create a new branch.

lets say we are currently in master branch with a file app.py.

now we created a branch testbranch.

we can make changes to app.py in testbranch but these changes will not be visible in the master branch. 
and any changes we apply in master branch will not be visible here.

after we verified our changes are woriking fine we can merge these branches.
```
1. to create a new branch :
    * git branch branchname
2. to activate a branch :
    * git checkout branchname
3. we can ceate and activate a branch in a sinlge command :
    * git checkout -b dummy
4. to delete a branch (should be done from master branch ):
    * git branch -d dummy 

![image](https://user-images.githubusercontent.com/93826731/180905295-7db92b51-4f1c-4621-8254-3d21367e2ccd.png)

**Merging**
to merge branches : 

1. go to the branch to which you want to merge the branches.
2. command  : git merge branchname

```
suppose we want to merge the testbranch code to master branch:
-- activate master branch 
-- git merge testbranch

```


### HEAD
```
HEAD points to most recent commit in most of the cases.
$ git show HEAD    ==> This will show the most recent commit details
$ git show HEAD~1  ==> most recent 2nd commit
HEAD is used for short notation of Commit id.

```

$ git difftool HEAD~1 HEAD~2

above command will show what are the  changes made between those commits

Detached Head:

when we move head from most recent commit to some other commit then ae are in detached head state.
any changes we made with detached head will not reflect to any other branches.


### .gitignore
```
when we want to ignore some files in our repository to be considered
we create a file named .gitignore
and place file names which needs tio be ignored in tht file.

let .gitignore has the following content

idea            ==> ignores idea folder
test.py         ==> ignores test.py file
*.exe           ==> ignores all files with .exe  extension

```
### Pull request

