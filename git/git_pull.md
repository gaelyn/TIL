If you push a branch to GitHub and another developer pushes changes to the same remote branch, `git pull` from main (or master) and checkout your local branch.  
You should have a message like
```
Your branch is behind 'origin/<your branch name>' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)
```
Now from your local branch type `git pull` and it will pull in changes from that remote branch `origin/<your branch name>`
