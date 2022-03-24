# Git Config

```
git config --global user.name "Your Name"
git config --global user.email "Your EMail"
```

# Setup a new Git project

Let's say you have an empty folder which you want to use a directory for a future project or if you already have a project that you are working on and want to start managing it with git. Use the following:

```
cd directoryforproject
git init
```
This will initialize an empty Git repository in the location you navigated to. Use `ls -la` to check if a `.git` folder has been created. 

## Staging and committing files

```
git add FILENAME
# git add --all
# git add -A
# git add . ----> Linux

git commit -m "First Commit"

```

## Files States

- Tracked
    - Unmodified
    - Modified
    - Staged
- Untracked

## git status

Use this to check file states and check changes.

```
git status
```
## Restoring Files


```
git restore FILENAME
# git restore .
# git checkout .

git restore --staged filename # unstage
git restore filename # undo changes
```
`restore` will not work with untracked files. If you want to remove the addition of new untracked file, you will need to delete it manually.

## Change from master to main

```
git branch -m master main
```

## .gitignore

For ignoring files in the same directory as the Git project. You may want to ignore some files such as 

- Sensitive info
- Personal notes
- System files (eg: vscode config files, macOS files such DS_Store etc.)

```
.DS_Store
.vscode/
authentication.js
node_modules
notes/
**/*-todo.md
```

Git does not track empty folder. 

# Environments

- Working
- Staging
- Commit

## Creating a Global Ignore File

```
git config --global core.excludesfile [file]
```

## Clearing the cache

```
git rm -r --cached .
```
`.` for the current directory, would need to do a `git add .`  and then a `git commit -m "MESSAGE"` again. 

# Deleting and Renaming files

## Deleting files
Manually delete it or

```
git rm index.html
```

What this would do is that it would move the deleted file automatically to staging. So it saves one step as compared to when manually deleting the file. 

## Renaming files

```
git mv oldfilename newfilename
```
# Git diff command

```
git diff
```

```
git log
git log --oneline #for shorter log view
```
# Changing History

## Amending

What happens if you commit something incorrect, can it be changed? One option is to commit the correction but that will create a "messy" history. Git allows the user to amend this.

```
git commit -amend #amend flag
git commit -am 'New commit message'
git commit -amend --no-edit #leave the message same as last time
```

## Reset
Resetting lets you get back to the previous commit or rewind. 

```
git reset hashfromlog
```
This won't rewind the changes you made to the files (if any). Use `git status` to see what's up. What if you want to undo those file changes as well just not the commit? Use the hard reset option.

```
git reset --hard hashfromlog
```

## Rebasing

```
git rebase <branch>/<commit>
# git rebase --interactive <branch>/<commit>
# git rebase -i HEAD-#
# git rebase -i --root
```

# Branches

Different versions of your code

```
git branch
```
## Copying a branch

```
git switch -c NAME
# git checkout -b NAME #Old use
```

## Merging a branch

```
git merge <branch>
```

## Deleting a branch

```
git branch --delete NAME
# git branch -d NAME ---> use as long as branch is free of conflicts
# git branch -D NAME ---> forces git to just delete the branch
```

This is *Git Flow*
- Feature/fix branch
- Make changes
- Merge to master
- Delete old branch

While collaborating, every collaborator can create a new branch, make changes and then merge to master after their work is done. 

# Conflicts!

Merge conflicts happen when two or more users fix the same item in the project. Let's say User1 created branch1 and User2 created branch2. Both the users made changes/ fixed file named 'foo'. User1 committed (merged) this change to master branch and later User2 does the same ---- this is where the conflict arises! Let's see how to deal with that.

# Stash and Clean

## Stashing code

Stash your fixed/added code in a place and go back to before you made the changes. This maybe required when you do not want to lose the code that you have already worked on but you need to go back to the time when you had not made those changes.

SISO ---> Last in is index 0. 

```
git stash
# git stash list ---> What is stored?
# git stash apply ---> Retrieve the stash
# git stash pop ---> Remove the stash 
```

## Clean

```
git clean -n # dry run, safest use of clean, shows you what's going to be deleted
git clean -d # directories

git clean -dn # shows untracked files and directories
git clean -df $ removes untracked files and directories
git clean -f # force
```