- [Add new credential and erase old credential](#add-new-credential-and-erase-old-credential)
- [Git merge reports "Already up-to-date" though there is a difference](#git-merge-reports-already-up-to-date-though-there-is-a-difference)
    - [Solution:](#solution)

# Add new credential and erase old credential

```bash
git config --global user.email '<git-commit-address>'
git config --global --unset credential.helper
```

# Git merge reports "Already up-to-date" though there is a difference

I have a git repository with 2 branches: master and test.
There are differences between master and test branches.
Both branches have all changes committed.

If I do:
```bash
git checkout master
git diff test
```
A screen full of changes appears showing the differences. I want to merge the changes in the test branch and so do:
```bash
git merge test
```
But get the message "Already up-to-date"

However, examining files under each different branch clearly shows differences.

What's the problem here and how do I resolve it?

### Solution:

The head will go from test to master, i.e. the changes will go from test to master, be careful with this!

The message “Already up-to-date” means that all the changes from the branch you’re trying to merge have already been merged to the branch you’re currently on. More specifically it means that the branch you’re trying to merge is a parent of your current branch. Congratulations, that’s the easiest merge you’ll ever do. :)

Use git to take a look at your repository. The label for the “test” branch should be somewhere below your “master” branch label.

Your branch is up-to-date with respect to its parent. According to merge there are no new changes in the parent since the last merge. That does not mean the branches are the same, because you can have plenty of changes in your working branch and it sounds like you do.

One solution to remediate the problem is:
```bash
git checkout master
git reset --hard test
```
This brings it back to the 'test' level.

Then do:

```bash
git push --force origin master
```

in order to force changes back to the central repo.