
<!-- @import "[TOC]" {cmd:"toc", depthFrom:1, depthTo:6, orderedList:false} -->

<!-- code_chunk_output -->

* [Git Help](#git-help)
	* [Clone Repo](#clone-repo)
	* [Fix filename too long error](#fix-filename-too-long-error)
	* [Pushing to online repo](#pushing-to-online-repo)
	* [Delete remote branch](#delete-remote-branch)
	* [Merge branchB into branchA](#merge-branchb-into-brancha)
	* [Rename Branch](#rename-branch)
	* [Create SubBranch](#create-subbranch)
	* [List Branches](#list-branches)
	* [See log of remote branch](#see-log-of-remote-branch)
	* [Undo Commits, Reapply Later](#undo-commits-reapply-later)
	* [Remove all Uncommitted Changes](#remove-all-uncommitted-changes)
	* [See List of Tracked Files](#see-list-of-tracked-files)
	* [Tag a commit](#tag-a-commit)
	* [Create a remote origin](#create-a-remote-origin)

<!-- /code_chunk_output -->


# Git Help

## Make new branch

```sh
git checkout -b my-new-branch
```

## Clone Repo

```Bash
git clone ssh://<repo_url>
```

## Fix filename too long error

You'll probably have to run your shell as an administrator if in Windows

```Bash
git config --system core.longpaths true
```

## Pushing to online repo

```Bash
git checkout master
git pull
git checkout <your branch>
# just to make sure everything is committed
git commit -am "<commit message>"
# rebase to combine possible changes from others to master
git rebase master
git push origin <your branch>
```

After that, if you want to push to the remote master, do this (only after completing the previous step!):

```Bash
git checkout master
git merge devBranchName
git push
```

## Delete remote branch

```Bash
git push origin --delete branch_name
```

## Merge branchB into branchA

```Bash
git checkout branchA
git merge branchB
```

branchB can now be safely removed.

```Bash
git branch -d <branch path>
```

## Rename Branch
Current Branch:

```Bash
git branch -m newName

```

Other Branch:

```Bash
git branch -m oldName newName
```

## Create SubBranch

```Bash
git branch subBranchName parentBranchName
```

## List Branches

```Bash
# local branches
git branch
# remote branches
git branch -r
```

## See log of remote branch

```Bash
git log origin/master
```

## Undo Commits, Reapply Later

```Bash
# go back a commit
git reset --soft HEAD^
git stash save "name to be saved in stash"
# repeat as needed

# do whatever you need to do here

# reapply commits
git stash pop
git commit -am "title of commit to be reapplied"
# repeat as needed
```

## Remove all Uncommitted Changes
While in the master repository root:

```Bash
git checkout -- ./
```

## See List of Tracked Files

```Bash
git ls-tree --full-tree -r --name-only HEAD
```

## Tag a commit

```sh
git tag -a <tag/version> -m "your message"
```
To list tags, use:

```sh
git tag
```

## Create a remote origin

```sh
git remote add origin URL
git remote -v # verify

# first push
git push -u origin master
```

