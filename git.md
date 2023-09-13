# add new credential and erase old credential
```
git config --global user.email '<git-commit-address>'
git config --global --unset credential.helper
```
# to checkout to remote branch, you will need to fetch the contents of the branch using 
```
git fetch --all
```
first. Then use the same command
```
git checkout RemoteBranchName
```
