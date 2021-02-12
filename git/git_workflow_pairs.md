## Git workflow for pairs (or groups)
1. `git checkout -b name-of-branch` The `-b` creates a new branch and checks it out
2. Do what ever work your doing, making sure your work matches your branch name (if you make a branch called unicorn-class don't do work on medusa.rb)
3. `git add`
4. `git commit -m "Relevant commit message"`
5. `git push origin name-of-branch`
6. Click on link given in terminal or go to GitHub repo and create a pull request. Put any relevant info in message.
7. Add reviewer(s)
8. Reviewer(s) should check pull request and merge it.
9. Branch should be deleted after merging.
10. `git checkout main`
11. `git pull origin main`
