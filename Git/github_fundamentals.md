# To learn

- set up remote
- push
- pull

## Remotes

```
git remote add NAME URL
# git remote remove NAME
# git rename OLDNAME NEWNAME
# git remove -v  ----> verbose
```

## Git Push

```
git push REMOTE BRANCH
# git push --set-upstream-to origin main
git push -u origin main # --set-upstream
# git push --all
# git branch --set-upstream-to <origin/remote-branch>
```

## Clone, Fetch and Pull

```
git clone LINKTOTHEREPO
```
This allows you to get a repository onto your hard drive. 

```
git fetch
```
Synchronizes changes from the online repo onto your local hard drive. In case of branches present only on the remote repo, you can use `git branch -a` to see all the branches including the local and remote ones.

```
git pull
```
Before doing this, you must first set an upstream as mentioned earlier. The command is 

```
git branch --set-upstream-to=<remote>/<branch> main
```

Once you perform a pull, all of the changes in the remote version will reflect in the local version. 