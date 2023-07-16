### GIT AND GITHUB
---
**Git -** is a version control system (it is a technology) which lets you to track changes you make to your files over time.
**Github -** is an online hosting service for Git *repositories*.

A ==repository== is just another way to define a project being watched/tracked by Git.

 **1. Download Git for your OS:**
To check if git is installed on the computer :
> ```git``` OR ```git --version```

**2. Congfigure git on your system (needed only once):** 
Set your username and email address. Git will use this information to identify who made specific changes to files.
>```git config --global user.name "yourUsername"```
>```git config --global user.email "yourEmail"```

**3. Initialize your git repository:**

* ```ls``` -> lists all the contents in the pwd (present working directory).
* ```mkdir dirName``` -> creates a new folder in the pwd.
* ```cd dirName``` -> Enter the control to the directory to be made a git repository.

To make the pwd a git repository:
> ```git init```

==.git folder== contain hidden files which stores all the history and details of the project.
To find *.git folder* use:
> ```ls -a``` -> This shows all the hidden folders in the pwd.

To checkout the contents of .git folder : ```ls .git```

**3. Create a new file :** ```touch fileName.txt```

**4. Check for changes in git repo using git commands :**
>```git status```

The stages of a file being tracked by Git :
1. COMMITTED STATE
A file is in the committed state when all the changes made to the file have been saved in the local repo. Files in the committed stage are files ready to be pushed to the remote repo (on GitHub).
2. MODIFIED STATE
A file in the modified state has some changes made to it but it's not yet saved. This means that the state of the file has been altered from its previous committed state.
3. STAGED STATE
A file in the staged state means it is ready to be committed. In this state, all necessary changes have been made so the next step is to move the file to the commit state.

<span style="color: red">Untracked files (in red color) :</span>
* No one in the outer world (other than my system) knows that those files exist in the repository.
* There's no history of that file.

<span style="color: red"> Modified : </span>
* changes made in the file is to be tracked.

**5. Staging the files :**
Staging a file means that the history of the file will now be tracked by Git. The file is ready to be committed.
> ```git add .```
To stage all the files in the repo

> ```git add fileName```
To stage a single file

If a file gets staged by mistake, to undo it :
>```git restore --staged fileName.txt```

**6. Committing the changes :**
Committing the changes means saving the changes/progress of a particular project in the local repo. The files are ready to be pushed to the remote repo (on Github).
>```git commit -m "commit msg which is reflected in Github"```

- So basically four major steps are involved:
    1. Change
    2. Check (```git status```)
    3. Stage (```git add .```)
    4. Commit (```git commit -m "msg"```)

**7. To view the history of the project :**
> ```git log```

It displays all the commits made to the project with there hash IDs in case we need to revert back to that commit/version of the project.

---
>```vi fileName.txt```
Using vim editor to edit a files

>```cat fileName.txt```
To display contents of a file on the CLI/bash.

>```rm -rf fileName.txt```
To delete a file from the project.
---

#### GOING BACK TO A PREVIOUS VERSION/COMMIT OF PROJECT
* To undo any modification we did in our project.
* We cannot undo any particular commit.
* We have to undo the whole commits till that commit state which we want our repo to be.

**1. Get the hash ID of the commit which we want to restore from:**
>```git log```

**2. Then :**
>```git reset hashID```

All the changes made after that commit hashID are now unstaged. 

---
#### Attaching a local repo with a github account
Connecting a local repository to its remote repository (on Github):

**1. Add origin URL :**
>```git remote add origin <URL>```
```origin ->``` acts like a variable in which the URL that I am going to add to my git repo is saved (just like a contact name for a phone number. This can be named anything). 

By convention all the repositories and folders which are in your personal github account (that starts with github.com/yourName/repo) have their url named 'origin'.

To view all the URLs attached to the system folder:
>```git remote -v```

**2. Push the commits to the Origin :**

First change your main branch's name to "main". The default branch might be created as "master", but "main" is the standard name.
>```git branch -M main```


To update my system changes into my URL/github account :
>```git push -u origin main```  

```origin ->``` puch commit to which URL?
```main ->``` which branch to push to the origin?
Refresh the browser to see the changes!

*Note: It is advisible to first create a new repository in Github and then link its URL to your system's repository.* 

#### BRANCHES IN GIT
Ref: https://learngitbranching.js.org/
* By default the working branch is =='main'== (previously called 'master').
* Always create a new branch while making changes in the project (working on new features, removing bug etc).
* You should NEVER commit on main branch, as it is the production branch i.e., used by public so that any error in our new untested code do not effect the main branch.
* All code that are not finalized should go on a separate branch so that users of main branch (public) is not affected.

> To create a new branch:
>```git branch branchName```

> To move the Head to a particular branch:
>```git checkout branchName```

Now the Head is pointing to that particular branch.
The 'Head' is just a pointer which represents that all new changes will be made to the Head (i.e., the branch it is pointing to, can be 'main' or any other branch).
Thus, any commit made now will affect only that particular branch pointed by the 'Head'.

> Going back to main branch:
>```git checkout main```

**Merging a branch with the main branch :**
This is done after testing and finalizing changes for the users to see.
>```git merge branchName```
---
#### WORKING WITH EXISTING PROJECTS

1. You cannot directly make changes to anyone's project (Github repository). You have to create a fork from the original project Github repository. 

```Fork ->``` To create a copy of a project in my own Github account.

Looks something like this:
```yourName/Project-Name```
```forked from Microsoft/Project-Name```

You can now make any changes to that project.
*Note that any Github repo which starts with your username, its URL will be* ```origin.```

2. Now you need to bring that forked project from your Github account to your computer/system i.e., ==cloning the github repo:==
    i) First, copy the project URL which is in your account from ```Code -> Copy (under clone)```.
    ii) In CLI:
    >```git clone URL```
    This downloads all the files and folders of the project to your system/work-station.
---

```origin```- refers to the URL of your personal account project.
The URL to the original project repo ```Microsoft/Project-Name``` is known as ```upstream``` URL by convention. 

Add the URL of the original project repo to your forked repo:
>```git remote add upstream <URL-of-real-project>```
---
#### STASH 
If we want to save all our progress without making a commit (and dont want to loose it while making new changes), say to try something new and get back our original progress when required, we save our progress to stash:
>```git add .```
>```git status```
>```git stash```
>```git status``` -> this will show working tree clean

To bring back the saved original progress :
>```git stash pop```

To delete the saved progress and clear the stash :
>```git stash clear```

###### Example:
To go back to a particular version:
>```git log```
```git reset hashID```

All the changes after that commit hashID are now unstaged.
>```git status```
>```git add .```
>```git stash```

Now, if I push this to origin, I have to force push it because the online repository contains a commit which mine local repository does not (Commits are interlinked).
So force push : ```git push origin bugfix -f```

---
#### PULL REQUESTS
1. To make changes to a project, always create a new branch (i.e., never commit on the 'main' branch).
>```git branch bugfix```
>```git checkout bugfix```

2. All commits will now be made to the 'bugfix' branch:
>```git add .```
>```git commit -m 'Bugs fixed'```

3. Now push it to the 'origin' (your Github account):
>```git push origin <branchNametobePushed>```
>Here :```git push origin bugfix```

4. Now, Compare and generate a Pull Request to the original project Github repository.

* Why you should always create a new branch for any small changes?
If a branch already has an open pull request associated with it, it will not allow any new PR. All new commits will be added to that PR.

5. Pull request gets merged by the original project handler.
Changes made to ```yourName/Project-Name bugfix branch``` is now visible in the original project main branch.
---
To check if my repo is up to date with the origin project repo:
>```git checkout main```
>```git status```
>```git fetch --all --prune```

```all```- this option means to fetch all branches.
```prune```- this means to also fetch branches which are deleted.



