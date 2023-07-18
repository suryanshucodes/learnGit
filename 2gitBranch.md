#### BRANCHES IN GIT
---

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

**Merging a branch with the main branch :**
This is done after testing and finalizing changes for the users to see.

> Going back to main branch:
>```git checkout main```

>```git merge branchName```
---
