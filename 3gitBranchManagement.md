
### Git Branch Management
---
>```git branch```

This command returns a simple listing of your current branches.
The ```*``` character that prefixes a branch indicates that you currently have checked out that branch (i.e., the branch that ```HEAD``` points to). This means that if you commit at this point, that branch will be moved forward with your new work.

>```git branch -v```
Returns the last commit on each branch.

>```git branch --merged```
To see which branches are already merged into the branch you're currently on.

Branches on this list without the ```*``` in front of them are generally fine to delete with ```git branch -d branchName```; you’ve already incorporated their work into another branch, so you’re not going to lose anything.

>```git branch --no-merged```

To see branches which contain work that isn’t merged in the current branch yet, trying to delete it with ```git branch -d branchName``` will fail.

###### TIP:
To list directly what branches are not merged/merged into a particular branch without checking out that branch first: 
>```git branch --no-merged branchName```
---
### CHANGING BRANCH NAME
Note: Do not rename branches that are still in use by other collaborators.

1. Rename the branch name locally:
>```git branch --move old-Br-Name new-Br-Name```

2. To let others see the corrected branch on the remote, push it:
>```git push --set-upstream origin new-Br-Name```

Display all the local/remote branches:
>```git branch --all```

You can see that the branch with the old-branch-name is also still available remotely. To delete the old name branch remotely:
>```git push origin --delete old-Br-Name```

#### CHANGING THE ```master``` BRANCH NAME
Warning: Changing the name of a branch like master/main/mainline/default will break the integrations, services, helper utilities and build/release scripts that your repository uses.

Rename your local ```master``` branch to ```main```:
>```git branch --move master main```

To let others see the new main branch, push it to the remote:
>```git push --set-upstream origin main```

Your local master branch is gone, as it’s replaced with the main branch. However, the old master branch is still present on the remote.

Delete the remote master branch after making sure all the dependencies on it are removed:
>```git push origin --delete master```


