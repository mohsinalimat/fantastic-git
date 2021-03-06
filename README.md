fantastic-git
==

![](Screenshots/Banner.png)

Contents
==

<!-- TOC depthFrom:1 depthTo:3 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Reading :notebook_with_decorative_cover:](#reading-notebookwithdecorativecover)
- [Repos](#repos)
- [GitHub](#github)
- [Commands](#commands)
	- [Tag :1234:](#tag-1234)
	- [Remote :cloud:](#remote-cloud)
	- [Branch :tanabata_tree:](#branch-tanabatatree)
	- [Commit :pencil2:](#commit-pencil2)
	- [Reflog](#reflog)
	- [Revert](#revert)
	- [Checkout :checkered_flag:](#checkout-checkeredflag)
	- [Stash :package:](#stash-package)
	- [Rebase :wind_chime:](#rebase-windchime)
	- [.gitignore :honey_pot:](#gitignore-honeypot)
	- [Index :card_index:](#index-cardindex)
	- [Misc :ghost:](#misc-ghost)

<!-- /TOC -->

# Reading :notebook_with_decorative_cover:

- [Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/setting-up-a-repository)
- [git-cheat-sheet](https://github.com/arslanbilal/git-cheat-sheet)
- [Learn Enough Git to Be Dangerous](http://www.learnenough.com/git-tutorial)
- [Git Workflows for Pros: A Good Git Guide](http://www.toptal.com/git/git-workflows-for-pros-a-good-git-guide)
- [Git from the inside out](https://codewords.recurse.com/issues/two/git-from-the-inside-out)
- [git-game](https://github.com/git-game/git-game)
- [Introduction to Git - talk by Scott Chacon](https://www.youtube.com/watch?v=xbLVvrb2-fY)
- [Git Tutorial – Git Fu With The Command Line](http://www.raywenderlich.com/74258/git-tutorial-intermediate)
- [Git Immersion](http://gitimmersion.com/)

# Repos

- [gitflow](https://github.com/nvie/gitflow) Git extensions to provide high-level repository operations for Vincent Driessen's branching model
- [diff-so-fancy](https://github.com/so-fancy/diff-so-fancy) Good-lookin' diffs with diff-highlight and more

# GitHub

- [gitify](https://github.com/ekonstantinidis/gitify) GitHub Notifications on your menu bar.
- [twitter-for-github](https://github.com/bevacqua/twitter-for-github) Twitter handles for GitHub
- [octotree](https://github.com/buunguyen/octotree) Code tree for GitHub and GitLab
- [isometric-contributions](https://github.com/jasonlong/isometric-contributions) Render an isometric pixel art version of your contribution graph in Chrome and Safari.
- [github-s3](https://github.com/hyperoslo/github-s3) Shell scripts that make it really easy to archive and restore repositories between GitHub and AWS S3
- [mention-bot](https://github.com/facebook/mention-bot) Automatically mention potential reviewers on pull requests.
- [github-extended](https://github.com/onmyway133/github-extended) A Chrome extension to discover more repositories

# Commands

## Tag :1234:

#### List all tags

```
git tag
```

#### Tag a commit

```
git tag -a v1.4 -m "my version 1.4"
```

#### Delete remote tags

- [How to delete a remote tag?](http://stackoverflow.com/a/5480292/1418457)

```
git push --delete origin tagname
```

```
git push origin :tagname
```

#### Push tag to remote

- [Push a tag to a remote repository using Git?](http://stackoverflow.com/a/5195913/1418457)

```
git push origin tagname
```

#### Rename tag

- [How do you rename a Git tag?](http://stackoverflow.com/a/5719854/1418457)

```
git tag new old
git tag -d old
git push origin :refs/tags/old
git push --tags
```

#### Move tag from one commit to another commit

- [How can I move a tag on a git branch to a different commit?](http://stackoverflow.com/a/8044605/1418457)

```
git push origin :refs/tags/<tagname>
git tag -fa tagname
git push origin master --tags
```

## Remote :cloud:

#### List all remote

```
git remote
```

#### Rename remote

- [Renaming a remote](https://help.github.com/articles/renaming-a-remote/)

```
git remote rename old new
```

## Branch :tanabata_tree:

#### List all branches

```
git branch
```

#### Create a branch

- [Create a new branch with git and manage branches](https://github.com/Kunena/Kunena-Forum/wiki/Create-a-new-branch-with-git-and-manage-branches)

Create the branch on your local machine and switch in this branch

```
git checkout -b branch_name
```


#### Create branch from commit

- [Branch from a previous commit using git](http://stackoverflow.com/a/2816728/1418457)

```
git branch branch_name sha1_of_commit
```

#### Push the branch to remote

```
git push origin branch_name
```

#### Rename local branch

- [How do you rename the local branch?](http://stackoverflow.com/a/6591218/1418457)

Rename other branch

```
git branch -m old new
```

Rename current branch

```
git branch -m new
```

#### Rename remote branch

- [Rename master branch for both local and remote Git repositories](http://stackoverflow.com/a/16220970/1418457)

```
git branch -m old new                # Rename branch locally    
git push origin :old                 # Delete the old branch    
git push --set-upstream origin new   # Push the new branch, set local branch to track the new remote
```

#### Delete a branch

- [Delete a Git branch both locally and remotely](http://stackoverflow.com/a/10999165/1418457)

```
git branch -D the_local_branch
```

```
git push origin :the_remote_branch
```

## Commit :pencil2:

#### Undo last commit

- [How do you undo the last commit?](http://stackoverflow.com/a/6866485/1418457)

```
git reset --hard HEAD~1
```

#### Squash last n commits into one commit

- [Squash my last X commits together using Git](http://stackoverflow.com/questions/5189560/squash-my-last-x-commits-together-using-git)

```
git rebase -i HEAD~5
```

```
git reset --soft HEAD~5
git add .
git commit -m "Update"
git push -f origin master
```

#### Move last commits into new branch

- [Move the most recent commit(s) to a new branch with Git](http://stackoverflow.com/questions/1628563/move-the-most-recent-commits-to-a-new-branch-with-git)

```
git branch newbranch
git reset --hard HEAD~3 # Go back 3 commits. You *will* lose uncommitted work.*1
git checkout newbranch
```

#### Pick

- [CHERRY-PICKING EXPLAINED](http://think-like-a-git.net/sections/rebase-from-the-ground-up/cherry-picking-explained.html)

```
git cherry-pick hash_commit_A hash_commit_B
```

## Reflog

- [git-reflog](https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog)
- [Use “git reflog” and “git cherry-pick” to restore lost commits](http://www.ocpsoft.org/tutorials/git/use-reflog-and-cherry-pick-to-restore-lost-commits/)


#### Show reflog

```
git reflog
```

#### Get commit

```
git reset --hard 0254ea7
```

```
git cherry-pick 12944d8
```

## Revert

- [Revert previous commits](http://stackoverflow.com/a/21718540/1418457)

```
git revert --no-commit 0766c053..HEAD
git commit
```

#### Amend

- [Edit an incorrect commit message in Git](http://stackoverflow.com/questions/179123/edit-an-incorrect-commit-message-in-git)

```
git commit --amend
```

```
git commit --amend --no-edit
```

```
git commit --amend -m "New commit message"
```

- [Changing git commit message after push](http://stackoverflow.com/questions/8981194/changing-git-commit-message-after-push-given-that-no-one-pulled-from-remote)

```
git commit --amend -m "New commit message"
git push --force <repository> <branch>
```

## Checkout :checkered_flag:

#### Checkout a tag

```
git checkout tagname
```

```
git checkout -b newbranchname tagname
```

#### Checkout a branch

```
git checkout destination_branch
```

Use -m if there is merge conflict

```
git checkout -m master // from feature branch to master
```

#### Checkout a commit

```
git checkout commit_hash
```

```
git checkout -b newbranchname HEAD~4
```

```
git checkout -b newbranchname commit_hash
```

```
git checkout commit_hash file
```

## Stash :package:

- [6.3 Git Tools - Stashing](https://git-scm.com/book/en/v1/Git-Tools-Stashing)

#### Stash

```
git stash save "stash name"
```

```
git stash
```

#### List all stashes

```
git stash list
```

#### Apply a stash


```
git stash pop
```

```
git stash apply
```

```
git stash apply stash@{2}
```

## Rebase :wind_chime:

#### rebase
```
git rebase base // rebase the current branch onto base
```

## .gitignore :honey_pot:

#### Untrack

- [Making git “forget” about a file that was tracked but is now in .gitignore](http://stackoverflow.com/a/19095988/1418457)

```
git rm -r --cached .
git add .
git commit -am "Remove ignored files"
```

## Index :card_index:

#### Remove untracked files

```
git clean
```

#### Remove file from index

```
git reset file
```

#### Reset the index to match the most recent commit

```
git reset
```

#### Reset the index and the working directory to match the most recent commit

```
git reset --hard
```

## Misc :ghost:

#### Conflicting git rebase

- [How to get “their” changes in the middle of conflicting Git rebase?](http://stackoverflow.com/questions/8146289/how-to-get-their-changes-in-the-middle-of-conflicting-git-rebase)

```
git checkout --ours foo/bar.java
git add foo/bar.java
```

#### Resolve git merge conflict

- [Resolve Git merge conflicts in favor of their changes during a pull](http://stackoverflow.com/questions/10697463/resolve-git-merge-conflicts-in-favor-of-their-changes-during-a-pull)

#### theirs

- [Is there a “theirs” version of “git merge -s ours”?](http://stackoverflow.com/questions/173919/is-there-a-theirs-version-of-git-merge-s-ours)

```
git pull -X theirs
```

```
git checkout --theirs path/to/the/conflicted_file.php
```

```
git checkout --theirs .
git add .
```

```
git checkout branchA
git merge -X theirs branchB
```

#### Merge from master into feature branch after push

- [Git merge master into feature branch](http://stackoverflow.com/a/16957483/1418457)

```
git checkout feature1
git merge --no-ff master
```

Licence
--
This project is released under the MIT license. See LICENSE.md.
