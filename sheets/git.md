Git and Git Flow Cheat Sheet [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
===============
<hr>
<p align="center">
    <img alt="Git" src="./Img/git-logo.png" height="190" width="455">
</p>
<hr>

Git cheat sheet saves you from learning all the commands by heart.

Be free to contribute, update the grammar mistakes. You are also free to add your language file.

<hr>

Git Cheat Sheet English
===============
### Index
* [Set Up](#setup)
* [Configuration Files](#configuration-files)
* [Create](#create)
* [Local Changes](#local-changes)
* [Search](#search)
* [Commit History](#commit-history)
* [Move / Rename](#move--rename)
* [Branches & Tags](#branches--tags)
* [Update & Publish](#update--publish)
* [Merge & Rebase](#merge--rebase)
* [Undo](#undo)
* [Git Flow](#git-flow)


# A cheat sheet for Git workflows

![Git Cheat Sheet](https://raw.githubusercontent.com/hbons/git-cheat-sheet/master/preview.png)


<hr>

## Setup

##### Show current configuration:
```
$ git config --list
```
##### Show repository configuration:
```
$ git config --local --list
```

##### Show global configuration:
```
$ git config --global --list
```

##### Show system configuration:
```
$ git config --system --list
```

##### Set a name that is identifiable for credit when review version history:
```
$ git config --global user.name "[firstname lastname]"
```

##### Set an email address that will be associated with each history marker:
```
$ git config --global user.email "[valid-email]"
```

##### Set automatic command line coloring for Git for easy reviewing:
```
$ git config --global color.ui auto
```

##### Set global editor for commit
```
$ git config --global core.editor vi
```

<hr>

## Configuration Files

##### Repository specific configuration file [--local]:
```
<repo>/.git/config
```

##### User-specific configuration file [--global]:
```
~/.gitconfig
```

##### System-wide configuration file [--system]:
```
/etc/gitconfig
```

<hr>

## Create

##### Clone an existing repository:

There are two ways:

Via SSH

```
$ git clone ssh://user@domain.com/repo.git
```

Via HTTP

```
$ git clone http://domain.com/user/repo.git
```

##### Create a new local repository in the current directory:
```
$ git init
```

##### Create a new local repository in a specific directory:
```
$ git init <directory>
```

<hr>

## Local Changes

##### Changes in working directory:
```
$ git status
```

##### Changes to tracked files:
```
$ git diff
```

##### See changes/difference of a specific file:
```
$ git diff <file>
```

##### Add all current changes to the next commit:
```
$ git add .
```

##### Add some changes in &lt;file&gt; to the next commit:
```
$ git add -p <file>
```

##### Add only the mentioned files to the next commit:
```
$ git add <filename1> <filename2>
```

##### Commit all local changes in tracked files:
```
$ git commit -a
```

##### Commit previously staged changes:
```
$ git commit
```

##### Commit with message:
```
$ git commit -m 'message here'
```

##### Commit skipping the staging area and adding message:
```
$ git commit -am 'message here'
```

##### Commit to some previous date:
```
$ git commit --date="`date --date='n day ago'`" -am "<Commit Message Here>"
```

##### Change last commit:<br>
<em><sub>Don't amend published commits!</sub></em>

```
$ git commit -a --amend
```

##### Amend with last commit but use the previous commit log message
<em><sub>Don't amend published commits!</sub></em>

```shell
$ git commit --amend --no-edit
```

##### Change committer date of last commit:
```
GIT_COMMITTER_DATE="date" git commit --amend
```

##### Change Author date of last commit:
```shell
$ git commit --amend --date="date"
```

##### Move uncommitted changes from current branch to some other branch:<br>
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### Restore stashed changes back to current branch:
```shell
$ git stash apply
```

#### Restore particular stash back to current branch:
- *{stash_number}* can be obtained from `git stash list`

```shell
$ git stash apply stash@{stash_number}
```

##### Remove the last set of stashed changes:
```
$ git stash drop
```

<hr>

## Search

##### A text search on all files in the directory:
```
$ git grep "Hello"
```

##### In any version of a text search:
```
$ git grep "Hello" v2.5
```

##### Show commits that introduced a specific keyword
```
$ git log -S 'keyword'
```

##### Show commits that introduced a specific keyword (using a regular expression)
```
$ git log -S 'keyword' --pickaxe-regex
```

<hr>

## Commit History

##### Show all commits, starting with newest (it'll show the hash, author information, date of commit and title of the commit):
```
$ git log
```

##### Show all the commits(it'll show just the commit hash and the commit message):
```
$ git log --oneline
```

##### Show all commits of a specific user:
```
$ git log --author="username"
```

##### Show changes over time for a specific file:
```
$ git log -p <file>
```

##### Display commits that are present only in remote/branch in right side
```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### Who changed, what and when in &lt;file&gt;:
```
$ git blame <file>
```

##### Show Reference log:
```
$ git reflog show
```

##### Delete Reference log:
```
$ git reflog delete
```
<hr>

## Move / Rename

##### Rename a file:

Rename Index.txt to Index.html

```
$ git mv Index.txt Index.html
```

<hr>

## Branches & Tags

##### List all local branches:
```
$ git branch
```

#### List local/remote branches
```
$ git branch -a
```

##### List all remote branches:
```
$ git branch -r
```

##### Switch HEAD branch:
```
$ git checkout <branch>
```

##### Checkout single file from different branch
```
$ git checkout <branch> -- <filename>
```

##### Create and switch new branch:
```
$ git checkout -b <branch>
```

##### Switch to the previous branch, without saying the name explicitly:
```
$ git checkout -
```

##### Create a new branch from an exiting branch and switch to new branch:
```
$ git checkout -b <new_branch> <existing_branch>
```


#### Checkout and create a new branch from existing commit
```
$ git checkout <commit-hash> -b <new_branch_name>
```


##### Create a new branch based on your current HEAD:
```
$ git branch <new-branch>
```

##### Create a new tracking branch based on a remote branch:
```
$ git branch --track <new-branch> <remote-branch>
```

##### Delete a local branch:
```
$ git branch -d <branch>
```

##### Rename current branch to new branch name
```shell
$ git branch -m <new_branch_name>
```

##### Force delete a local branch:
<em><sub>You will lose unmerged changes!</sub></em>

```
$ git branch -D <branch>
```

##### Mark `HEAD` with a tag:
```
$ git tag <tag-name>
```

##### Mark `HEAD` with a tag and open the editor to include a message:
```
$ git tag -a <tag-name>
```

##### Mark `HEAD` with a tag that includes a message:
```
$ git tag <tag-name> -am 'message here'
```

##### List all tags:
```
$ git tag
```

##### List all tags with their messages (tag message or commit message if tag has no message):
```
$ git tag -n
```

<hr>

## Update & Publish

##### List all current configured remotes:
```
$ git remote -v
```

##### Show information about a remote:
```
$ git remote show <remote>
```

##### Add new remote repository, named &lt;remote&gt;:
```
$ git remote add <remote> <url>
```

##### Rename a remote repository, from &lt;remote&gt; to &lt;new_remote&gt;:
```
$ git remote rename <remote> <new_remote>
```

##### Remove a remote:
```
$ git remote rm <remote>
```

<em><sub>Note: git remote rm does not delete the remote repository from the server. It simply removes the remote and its references from your local repository.</sub></em>

##### Download all changes from &lt;remote&gt;, but don't integrate into HEAD:
```
$ git fetch <remote>
```

##### Download changes and directly merge/integrate into HEAD:
```
$ git remote pull <remote> <url>
```

##### Get all changes from HEAD to local repository:
```
$ git pull origin master
```

##### Get all changes from HEAD to local repository without a merge:
```
$ git pull --rebase <remote> <branch>
```

##### Publish local changes on a remote:
```
$ git push <remote> <branch>
```

##### Delete a branch on the remote:
```
$ git push <remote> :<branch> (since Git v1.5.0)
```
OR
```
$ git push <remote> --delete <branch> (since Git v1.7.0)
```

##### Publish your tags:
```
$ git push --tags
```
<hr>

#### Configure the merge tool globally to meld (editor)
```bash
$ git config --global merge.tool meld
```

##### Use your configured merge tool to solve conflicts:
```
$ git mergetool
```

## Merge & Rebase

##### Merge branch into your current HEAD:
```
$ git merge <branch>
```

#### List merged branches
```
$ git branch --merged
```

##### Rebase your current HEAD onto &lt;branch&gt;:<br>
<em><sub>Don't rebase published commit!</sub></em>

```
$ git rebase <branch>
```

##### Abort a rebase:
```
$ git rebase --abort
```

##### Continue a rebase after resolving conflicts:
```
$ git rebase --continue
```

##### Use your editor to manually solve conflicts and (after resolving) mark file as resolved:
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### Squashing commits:
```
$ git rebase -i <commit-just-before-first>
```

Now replace this,

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

to this,

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```
<hr>

## Undo

##### Discard all local changes in your working directory:
```
$ git reset --hard HEAD
```

##### Get all the files out of the staging area(i.e. undo the last `git add`):
```
$ git reset HEAD
```

##### Discard local changes in a specific file:
```
$ git checkout HEAD <file>
```

##### Revert a commit (by producing a new commit with contrary changes):
```
$ git revert <commit>
```

##### Reset your HEAD pointer to a previous commit and discard all changes since then:
```
$ git reset --hard <commit>
```

##### Reset your HEAD pointer to a remote branch current state.
```
$ git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### Reset your HEAD pointer to a previous commit and preserve all changes as unstaged changes:
```
$ git reset <commit>
```

##### Reset your HEAD pointer to a previous commit and preserve uncommitted local changes:
```
$ git reset --keep <commit>
```

##### Remove files that were accidentally committed before they were added to .gitignore
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```
<hr>

## Git-Flow
Improved [Git-flow](https://github.com/petervanderdoes/gitflow-avh)

### Index
* [Setup](#setup)
* [Getting Started](#getting-started)
* [Features](#features)
* [Make a Release](#make-a-release)
* [Hotfixes](#hotfixes)
* [Commands](#commands)

<hr>

### Setup
###### You need a working git installation as prerequisite. Git flow works on OSX, Linux and Windows.

##### OSX Homebrew:
```
$ brew install git-flow-avh
```

##### OSX Macports:
```
$ port install git-flow
```

##### Linux (Debian-based):
```
$ sudo apt-get install git-flow
```

##### Windows (Cygwin):
###### You need wget and util-linux to install git-flow.
```bash
$ wget -q -O - --no-check-certificate https://raw.githubusercontent.com/petervanderdoes/gitflow/develop/contrib/gitflow-installer.sh install <state> | bash
```
<hr>

### Getting Started
###### Git flow needs to be initialized in order to customize your project setup. Start using git-flow by initializing it inside an existing git repository:
##### Initialize:
###### You'll have to answer a few questions regarding the naming conventions for your branches. It's recommended to use the default values.
```shell
git flow init
```
OR
###### To use default
```shell
git flow init -d
```
<hr>

### Features
###### Develop new features for upcoming releases. Typically exist in developers repos only.
##### Start a new feature:
###### This action creates a new feature branch based on 'develop' and switches to it.
```
git flow feature start MYFEATURE
```

##### Finish up a feature:
###### Finish the development of a feature. This action performs the following:
###### 1) Merged MYFEATURE into 'develop'.
###### 2) Removes the feature branch.
###### 3) Switches back to 'develop' branch
```
git flow feature finish MYFEATURE
```

##### Publish a feature:
###### Are you developing a feature in collaboration? Publish a feature to the remote server so it can be used by other users.
```
git flow feature publish MYFEATURE
```

##### Getting a published feature:
###### Get a feature published by another user.
```
git flow feature pull origin MYFEATURE
```

##### Tracking a origin feature:
###### You can track a feature on origin by using
```
git flow feature track MYFEATURE
```
<hr>

### Make a Release
###### Support preparation of a new production release. Allow for minor bug fixes and preparing meta-data for a release

##### Start a release:
###### To start a release, use the git flow release command. It creates a release branch created from the 'develop' branch. You can optionally supply a [BASE] commit sha-1 hash to start the release from. The commit must be on the 'develop' branch.
```
git flow release start RELEASE [BASE]
```
###### It's wise to publish the release branch after creating it to allow release commits by other developers. Do it similar to feature publishing with the command:
```
git flow release publish RELEASE
```
###### (You can track a remote release with the: ```git flow release track RELEASE``` command)

##### Finish up a release:
###### Finishing a release is one of the big steps in git branching. It performs several actions:
###### 1) Merges the release branch back into 'master'
###### 2) Tags the release with its name
###### 3) Back-merges the release into 'develop'
###### 4) Removes the release branch
```
git flow release finish RELEASE
```
###### Don't forget to push your tags with ```git push --tags```

<hr>

### Hotfixes
###### Hotfixes arise from the necessity to act immediately upon an undesired state of a live production version. May be branched off from the corresponding tag on the master branch that marks the production version.

##### Git flow hotfix start:
###### Like the other git flow commands, a hotfix is started with
```
$ git flow hotfix start VERSION [BASENAME]
```
###### The version argument hereby marks the new hotfix release name. Optionally you can specify a basename to start from.

##### Finish a hotfix:
###### By finishing a hotfix it gets merged back into develop and master. Additionally the master merge is tagged with the hotfix version
```
git flow hotfix finish VERSION
```
<hr>

### Commands
<p align="center">
    <img alt="Git" src="./Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="Img/git-flow-commands-without-flow.png">
</p>
<hr>



# Git

## Setup

### Git global setup

```bash
git config --global user.name "Prename Name"
git config --global user.email "email@example.com"
```

Just remove the `--global` flag for local setup.

### Create a new repository

```bash
git clone https://user@github.com/user/repo.git
cd repo
touch README.md
git add README.md
git commit -m "add README"
git push -u origin main
```

### Existing folder

```bash
cd existing_folder
git init
git remote add origin https://user@github.com/user/repo.git
git add .
git commit
git push -u origin main
```

### Existing Git repository

```bash
cd existing_repo
git remote add origin https://user@github.com/user/repo.git
git push -u origin --all
git push -u origin --tags
```

### Update remote location

```bash
git remote rm origin
git remote add origin <new-location>
git branch --set-upstream-to=origin/main main
```

### Stop tracking file

```bash
git update-index --assume-unchanged [path]
```

### Rename default branch of local clone

To update a local clone of a repository whose default branch name was changed (e.g. from `master` to `main`):

```bash
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

## Remove password prompt

Caution: this will store the password unencrypted on the disk! Only use if it's safe on your machine!

```bash
git config credential.helper store
```

## Sign/verify commits

Use `git commit -S` by default for all commits

```bash
git config --global commit.gpgsign true
```

Set default key

```bash
git config --global user.signingkey <key-id>
```

In case GPG failed to sign data

```bash
export GPG_TTY=$(tty)
```

## Tags

### Add tag to specific commit

```bash
git tag -a v[version] [hash] -m "your tag description"
```

### Show commits since last tag

```bash
git log $(git describe --tags --abbrev=0)..HEAD --oneline
```

## Branches

### Remove Branches

```bash
git branch -d local-branch-name
git remote prune origin
```

## Submodules

Pull all submodules of the current repository (as they will not automatically retrieved by a `git clone`)

```bash
git submodule update --init --recursive
```
Some useful aliases include:

| Alias | Command | What to Type |
| --- | --- | --- |
| `git cm` | `git commit` | `git config --global alias.cm commit` |
| `git co` | `git checkout` | `git config --global alias.co checkout` |
| `git ac` | `git add . -A` `git commit` | `git config --global alias.ac '!git add -A && git commit'` |
| `git st` | `git status -sb` | `git config --global alias.st 'status -sb'` |
| `git tags` | `git tag -l` | `git config --global alias.tags 'tag -l'` |
| `git branches` | `git branch -a` | `git config --global alias.branches 'branch -a'` |
| `git cleanup` | `git branch --merged \| grep -v '*' \| xargs git branch -d` | `git config --global alias.cleanup "!git branch --merged \| grep -v '*' \| xargs git branch -d"` |
| `git remotes` | `git remote -v` | `git config --global alias.remotes 'remote -v'` |
| `git lg` | `git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --` | `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --"` |

*Some Aliases are taken from [@mathiasbynens](https://github.com/mathiasbynens) dotfiles: https://github.com/mathiasbynens/dotfiles/blob/master/.gitconfig*

#### Auto-Correct
Git gives suggestions for misspelled commands and if auto-correct is enabled the command can be fixed and executed automatically. Auto-correct is enabled by specifying an integer which is the delay in tenths of a second before git will run the corrected command. Zero is the default value where no correcting will take place, and a negative value will run the corrected command with no delay.

For example, if you type `git comit` you will get this:

```bash
$ git comit -m "Message"
# git: 'comit' is not a git command. See 'git --help'.

# Did you mean this?
#   commit
```

Auto-correct can be enabled like this (with a 1.5 second delay):

```bash
$ git config --global help.autocorrect 15
```

So now the command `git comit` will be auto-corrected to `git commit` like this:

```bash
$ git comit -m "Message"
# WARNING: You called a Git command named 'comit', which does not exist.
# Continuing under the assumption that you meant 'commit'
# in 1.5 seconds automatically...
```

The delay before git will rerun the command is so the user has time to abort.

#### Color
To add more color to your Git output:

```bash
$ git config --global color.ui 1
```

[*Read more about the Git `config` command.*](http://git-scm.com/docs/git-config)

### Git Resources
| Title | Link |
| ----- | ---- |
| Official Git Site | http://git-scm.com/ |
| Official Git Video Tutorials | http://git-scm.com/videos |
| Code School Try Git | http://try.github.com/ |
| Introductory Reference & Tutorial for Git | http://gitref.org/ |
| Official Git Tutorial | http://git-scm.com/docs/gittutorial |
| Everyday Git | http://git-scm.com/docs/everyday |
| Git Immersion | http://gitimmersion.com/ |
| Git God | https://github.com/gorosgobe/git-god |
| Git for Computer Scientists | http://eagain.net/articles/git-for-computer-scientists/ |
| Git Magic | http://www-cs-students.stanford.edu/~blynn/gitmagic/ |
| Git Visualization Playground | http://onlywei.github.io/explain-git-with-d3/#freeplay |
| Learn Git Branching | http://pcottle.github.io/learnGitBranching/ |
| A collection of useful .gitignore templates | https://github.com/github/gitignore |
| Unixorn's git-extra-commands collection of git scripts | https://github.com/unixorn/git-extra-commands |

#### Git Books
| Title | Link |
| ----- | ---- |
| Pragmatic Version Control Using Git | https://pragprog.com/titles/tsgit/pragmatic-version-control-using-git |
| Pro Git | http://git-scm.com/book |
| Git Internals PluralSight | https://github.com/pluralsight/git-internals-pdf |
| Git in the Trenches | http://cbx33.github.io/gitt/ |
| Version Control with Git | http://www.amazon.com/Version-Control-Git-collaborative-development/dp/1449316387 |
| Pragmatic Guide to Git | https://pragprog.com/titles/pg_git/pragmatic-guide-to-git |
| Git: Version Control for Everyone | https://www.packtpub.com/application-development/git-version-control-everyone |

#### Git Videos
| Title | Link |
| ----- | ---- |
| Linus Torvalds on Git | https://www.youtube.com/watch?v=4XpnKHJAok8 |
| Introduction to Git with Scott Chacon | https://www.youtube.com/watch?v=ZDR433b0HJY |
| Git From the Bits Up | https://www.youtube.com/watch?v=MYP56QJpDr4 |
| Graphs, Hashes, and Compression, Oh My! | https://www.youtube.com/watch?v=ig5E8CcdM9g |
| GitHub Training & Guides | https://www.youtube.com/watch?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-&v=FyfwLX4HAxM |

#### Git Articles
| Title | Link |
| ----- | ---- |
| GitHub Flow  | http://scottchacon.com/2011/08/31/github-flow.html |
| Migrating to Git Large File Storate (Git LFS) | http://vooban.com/en/tips-articles-geek-stuff/migrating-to-git-lfs-for-developing-deep-learning-applications-with-large-files/ |

## FAQ

* [I want to show the status of the current branch.](#i-want-to-show-the-status-of-the-current-branch)
* [I want to create a new branch that is based on the current branch.](#i-want-to-create-a-new-branch-that-is-based-on-the-current-branch)
* [I want to checkout the previous branch that I was on.](#i-want-to-checkout-the-previous-branch-that-i-was-on)
* [I want to list the files that have been modified in the current working tree.](#i-want-to-list-the-files-that-have-been-modified-in-the-current-working-tree)
* [I want to view the changes that were made in a given commit.](#i-want-to-view-the-changes-that-were-made-in-a-given-commit)
* [I want to list the files that were changed in a given commit.](#i-want-to-list-the-files-that-were-changed-in-a-given-commit)
* [I want to view the changes that were made across multiple commits.](#i-want-to-view-the-changes-that-were-made-across-multiple-commits)
* [I want to view the changes that were made in a given file.](#i-want-to-view-the-changes-that-were-made-in-a-given-file)
* [I want to view the contents of a file in a given commit.](#i-want-to-view-the-contents-of-a-file-in-a-given-commit)
* [I want to open the contents of a file in a given commit in my editor.](#i-want-to-open-the-contents-of-a-file-in-a-given-commit-in-my-editor)
* [I want to copy a file from a given commit into my current working tree.](#i-want-to-copy-a-file-from-a-given-commit-into-my-current-working-tree)
* [I want to copy the last commit from another branch into my branch.](#i-want-to-copy-the-last-commit-from-another-branch-into-my-branch)
* [I want to copy an earlier commit from the current branch to the `head`.](#i-want-to-copy-an-earlier-commit-from-the-current-branch-to-the-head)
* [I want to update the files in the current commit.](#i-want-to-update-the-files-in-the-current-commit)
* [I want to edit the current commit message.](#i-want-to-edit-the-current-commit-message)
* [I want to copy `master` into my feature branch.](#i-want-to-copy-master-into-my-feature-branch)
* [I want to revert the merge of my feature branch into `master`.](#i-want-to-revert-the-merge-of-my-feature-branch-into-master)
* [I want to extract changes that I accidentally made to `master`.](#i-want-to-extract-changes-that-i-accidentally-made-to-master)
* [I want to undo the changes that I've made to my branch.](#i-want-to-undo-the-changes-that-ive-made-to-my-branch)
* [I want to remove unpublished changes from my branch.](#i-want-to-remove-unpublished-changes-from-my-branch)
* [I want to see which branches have already been merged into `master`.](#i-want-to-see-which-branches-have-already-been-merged-into-master)
* [I want to see which branches have not yet been merged into `master`.](#i-want-to-see-which-branches-have-not-yet-been-merged-into-master)
* [I want to delete my feature branch.](#i-want-to-delete-my-feature-branch)
* [I want to delete a remote branch.](#i-want-to-delete-a-remote-branch)
* [I want to update `master` because my `push` was rejected.](#i-want-to-update-master-because-my-push-was-rejected)
* [I want to remove a file from my staging area.](#i-want-to-remove-a-file-from-my-staging-area)
* [I want to squash several commits into one (or more) commits.](#i-want-to-squash-several-commits-into-one-or-more-commits)
* [I want to squash several commits into one commit without using `rebase`.](#i-want-to-squash-several-commits-into-one-commit-without-using-rebase)
* [I want to temporarily set-aside my feature work.](#i-want-to-temporarily-set-aside-my-feature-work)
* [I want to keep my changes during conflict resolution.](#i-want-to-keep-my-changes-during-conflict-resolution)
* [I want to find the commit that deleted a file.](#i-want-to-find-the-commit-that-deleted-a-file)
* [I want to find the commit that deleted a file that contained a piece of code.](#i-want-to-find-the-commit-that-deleted-a-file-that-contained-a-piece-of-code)

## Use Cases

### I want to show the status of the current branch.

The `status` command shows differences between the working tree, the index, and `head` commit.

```sh
git status
```

### I want to create a new branch that is based on the current branch.

In general, you want to implement new features in short-lived "feature branches" so that changes can be isolated. You can use the `checkout` command to create a new branch based on the current branch:

```sh
git checkout master

# Creates a new branch, `my-feature`, based on `master`.
git checkout -b my-feature
```

### I want to checkout the previous branch that I was on.

In some of the `git` commands, the `-` token refers to the "last branch" that you had checked-out. This makes it very easy to jump back-and-forth between two branches:

```sh
git checkout master
git checkout my-feature

# At this point, the `-` refers to the `master` branch.
git checkout -

# At this point, the `-` refers to the `my-feature` branch.
git checkout -
```

The `-` token can also be used to merge-in the last branch that you had checked-out:

```sh
git checkout my-feature
# ... changes to the working tree (your file system).
git add .
git commit -m "Awesome updates."
git checkout master

# At this point, the `-` refers to the `my-feature` branch.
git merge -
```

The `-` token can also be used to `cherry-pick` the most recent commit of the last branch that you had checked-out:

```sh
git checkout my-feature
# ... changes to the working tree (your file system).
git add .
git commit -m "Minor tweaks."

git checkout master

# At this point, the `-` refers to the `my-feature` branch.
git cherry-pick -
```

### I want to list the files that have been modified in the current working tree.

By default, when you call `git diff`, you see all of the content that has been modified in the current working tree (and not yet staged). However, you can use the `--stat` modifier to simply list the files that have been modified:

```sh
git diff --stat
```

### I want to view the changes that were made in a given commit.

When `show` is given a branch name, it will default to `head` - the last or most-recent commit on the given branch:

```sh
git checkout master

# Outputs the changes made to the `head` commit of the current (`master`)
# branch.
git show

# Outputs the changes made to the `head` commit of the `my-feature` branch.
git show my-feature
```

You can also use the `show` command to target a specific commit that is not the `head` commit. This can be done with a specific commit hash; or, a relative commit operator like `~`:

```sh
# Outputs the changes made in the commit with the given hash.
git show 19e771

# Outputs the changes made in in a previous commit of the current (`master`)
# branch.
git show head~ # Show changes in first parent.
git show head~~ # Show changes in first parent's first parent.
git show head~~~ # Show changes in first parent's first parent's first parent.

# Outputs the changes made in a previous commit of the `my-feature` branch.
git show my-feature~
git show my-feature~~
git show my-feature~~~
```

### I want to list the files that were changed in a given commit.

Just as with `git diff`, you can limit the output of the `git show` command using the `--stat` modifier. This will list the files that were changed in the given commit:

```sh
# Outputs the list of files changed in the commit with the given hash.
git show 19e771 --stat
```

### I want to view the changes that were made across multiple commits.

While the `show` command can show you changes in a given commit, you can use the `diff` command to show changes across multiple commits:

```sh
git checkout master

# Outputs the changes between `head~` and `head` of the current branch. If
# only one commit is provided, other commit is assumed to be `head`.
git diff head~

# Outputs the changes between the first commit and the second commit.
git diff head~~~..head~~
```

And, since branch names are really just aliases for commits, you can use a branch name in order to show the changes between one branch and your branch:

```sh
git checkout my-feature

# At this point, the following are equivalent and output the changes between
# the `head` commit of the `master` branch and the `head` commit of the
# `my-feature` branch.
git diff master
git diff master..head
git diff master..my-feature
```

### I want to view the changes that were made in a given file.

By default, the `show` command shows all of the changes in a given commit. You can limit the scope of the output by using the `--` modifier and identifying a filepath:

```sh
# Outputs the changes made to the `README.md` file in the `head` commit of the
# `my-feature` branch.
git show my-feature -- README.md

# Outputs the changes made to the `README.md` file in the `19e771` commit.
git show 19e771 -- README.md
```

### I want to view the contents of a file in a given commit.

By default, the `show` command shows you the changes made to a file in a given commit. However, if you want to view the entire contents of a file as defined at that time of a given commit, regardless of the changes made in that particular commit, you can use the `:` modifier to identify a filepath:

```sh
# Outputs the contents of the `README.md` file as defined in the `head` commit
# of the `my-feature` branch.
git show my-feature:README.md

# Outputs the contents of the `README.md` file as defined in the `19e771`
# commit.
git show 19e771:README.md
```

### I want to open the contents of a file in a given commit in my editor.

Since you're working on the command-line, the output of any git-command can be piped into another command. As such, you can use the `show` command to open a previous commit's file-content in your editor or viewer of choice:

```sh
# Opens the `README.md` file from the `head` commit of the `my-feature` branch
# in the Sublime Text editor.
git show my-feature:README.md | subl

# Opens the `README.md` file from the `19e771` commit in the `less` viewer.
git show 19e771:README.md | less
```

### I want to copy a file from a given commit into my current working tree.

Normally, the `checkout` command will update the entire working tree to point to a given commit. However, you can use the `--` modifier to copy (or checkout) a single file from the given commit into your working tree:

```sh
git checkout my-feature

# While staying on the `my-feature` branch, copy the `README.md` file from
# the `master` branch into the current working tree. This will overwrite the
# current version of `README.md` in your working tree.
git checkout master -- README.md
```

### I want to copy the last commit from another branch into my branch.

When you don't want to merge a branch into your current working tree, you can use the `cherry-pick` command to copy specific commit-changes into your working tree. Doing so creates a new commit on top of the current branch:

```sh
git checkout master

# Copy the `head` commit-changes of the `my-feature` branch onto the `master`
# branch. This will create a new `head` commit on `master`.
git cherry-pick my-feature
```

### I want to copy an earlier commit from the current branch to the `head`.

Sometimes, after you understand why reverted code was breaking, you want to bring the reverted code back into play and then fix it. You _could_ use the `revert` command in order to "revert the revert"; but, such terminology is unattractive. As such, you can `cherry-pick` the reverted commit to bring it back into the `head` where you can then fix it and commit it:

```sh
git checkout master

# Assuming that `head~~~` and `19e771` are the same commit, the following are
# equivalent and will copy the changes in `19e771` to the `head` of the 
# current branch (as a new commit).
git cherry-pick head~~~
git cherry-pick 19e771
```

### I want to update the files in the current commit.

If you want to make changes to a commit after you've already committed the changes in your current working tree, you can use the `--amend` modifier. This will add any staged changes to the existing commit.

```sh
git commit -m "Woot, finally finished!"

# Oops, you forgot a change. Edit the file and stage it.
# ... changes to the working tree (your file system).
git add oops.txt

# Adds the currently-staged changes (oops.txt) to the current commit, giving
# you a chance to update the commit message.
git commit --amend
```

### I want to edit the current commit message.

In addition to adding files to the current commit, the `--amend` modifier can also be used to change the current commit message:

```sh
git add .
git commit -m "This is greet."

# Oh noes! You misspelled "great". You can edit the current commit message:
git commit --amend -m "This is great."
```

Note that if you omit the `-m message` portion of this command, you will be able to edit the commit message in your configured editor.

### I want to copy `master` into my feature branch.

At first, you may be tempted to simply `merge` your `master` branch into your feature branch, but doing so will create an unattactive, non-intuitive, Frankensteinian commit tree. Instead, you should `rebase` your feature branch on `master`. This will ensure that your feature commits are cleanly colocated in the commit tree and align more closely with a human mental model:

```sh
git checkout my-feature

# This will unwind the commits specific to the `my-feature` branch, pull in
# the missing `master` commits, and then replay your `my-feature` commits.
git rebase master
```

Once your `my-feature` branch has been rebased on `master`, you could then, if you wanted to, perform a `--ff-only` merge ("fast forward only") of your feature branch back into `master`:

```sh
git checkout my-feature
git rebase master

# Fast-forward merge of `my-feature` changes into `master`, which means there
# is no creation of a "merge commit" - your `my-features` changes are simply
# added to the top of `master`.
git checkout master
git merge --ff-only my-feature
```

That said, when you're working on a team where everyone uses a different git workflow, you will definitely _want_ a "merge commit". This way, multi-commit merges can be easily reverted. To force a "merge commit", you can use the `--no-ff` modifier ("no fast forward"):

```sh
# Get the `my-feature` branch ready for merge.
git checkout my-feature
git rebase master

# Merge the `my-feature` branch into `master` creating a merge-commit.
git checkout master
git merge --no-ff my-feature
```

Now, if the merge needs to be reverted, you can simply revert the "merge commit" and all commits associated with the merge will be reverted.

### I want to revert the merge of my feature branch into `master`.

If you performed a `--ff-only` merge of your feature branch into `master`, there's no "easy" solution. You either have to reset the branch to an earlier commit (rewriting history); or, you have to revert the individual commits in the merge.

If, however, you performed a `--no-ff` merge ("no fast forward") that created a "merge commit", all you have to do is revert the merge commit:

```sh
git checkout master

# Merge the feature branch in, creating a "merge commit".
git merge --no-ff my-feature

# On noes! You didn't mean to merge that in. Assuming that the "merge commit"
# is now the `head` of `master`, you can revert back to the commit's fist
# parent, the `master` branch: -m 1. And, since `head` and `master` are the
# same commit, the following are equivalent:
git revert -m 1 head
git revert -m 1 master
```

### I want to extract changes that I accidentally made to `master`.

Sometimes, after you've finished working on your feature branch, you execute `git checkout master`, only find that you've been accidentally working on `master` the whole time (error: "Already on 'master'"). To fix this, you can `checkout` a new branch and `reset` your `master` branch:

```sh
git checkout master
# > error: Already on 'master'

# While on the `master` branch, create the `my-feature` branch as a copy of
# the `master` branch. This way, your `my-feature` branch will contain all of # your recent changes.
git checkout -b my-feature

# Now that your changes are safely isolated, get back into your `master`
# branch and `reset` it with the `--hard` modifier so that your local index
# and file system will match the remote copy.
git checkout master
git reset --hard origin/master
```

### I want to undo the changes that I've made to my branch.

If you've edited some files and then change your mind about keeping those edits, you can reset the branch using the `--hard` modifier. This will update the working tree - your file structure - to match the structure of the last commit on the branch (`head`).

**Caution**: You will lose data when using the `--hard` option.

```sh
git checkout my-feature
# ... changes to the working tree (your file system).
git add .

# Remove the file from staging AND remove the changes from the file system.
git reset --hard
```

If you call `git reset` without the `--hard` option, it will reset the staging to match the `head` of the branch, but it will leave your file system in place. As such, you will be left with "unstaged changes" that can be modified and re-committed.

### I want to remove unpublished changes from my branch.

If you've committed changes to the local copy of a remote (ie, published) branch, but you want to undo those changes, you can `reset` the local branch to match the remote branch:

```sh
git checkout my-feature

# Update the remote copy of the `my-feature` branch in order to make sure that
# you are working with the most up-to-date remote content.
git fetch origin my-feature

# Now, reset the local copy of `my-feature` to match the published copy. This
# will update your index and your local file system to match the published
# version of `my-feature`.
git reset --hard origin/my-feature
```

### I want to see which branches have already been merged into `master`.

From any branch, you can locate the merged-in branches (that can be safely deleted) by using the `--merged` modifier:

```sh
git checkout master

# List all of the local branches that have been merged into `master`. This
# command will be relative to the branch that you have checked-out.
git branch --merged
```

### I want to see which branches have not yet been merged into `master`.

From any branch, you can locate the unmerged branches by using the `--no-merged` modifier:

```sh
git checkout master

# List all of the local branches that have NOT YET been merged into `master`.
# This command will be relative the branch you have checked-out.
git branch --no-merged
```

### I want to delete my feature branch.

After you're merged your feature branch into `master`, you can delete your feature branch using the `branch` command:

```sh
# Merge your `my-feature` branch into `master` creating a "merge commit."
git checkout master
git merge --no-ff my-feature

# Safely delete the merged-in `my-feature` branch. The `-d` modifier will
# error-out if the given branch has not yet been merged into the current
# branch.
git branch -d my-feature
```

If you want to abandon a feature branch, you can use the `-D` modifier to force-delete it even if it has not yet been merged into `master`:

```sh
git checkout master

# Force-delete the `my-feature` branch even though it has not been merged
# into the `master` branch.
git branch -D my-feature
```

### I want to delete a remote branch.

When you delete a branch using `git branch -d`, it deletes your local copy; but, it doesn't delete the remote copy from your origin (ex, GitHub). To delete the remote copy, you have to `push` the branch using the `:` prefix:

```sh
git checkout master

# Safely delete the local copy of your `my-feature` branch. The `-d` modifier
# will error-out if the given branch has not been fully-merged into `master`.
git branch -d my-feature

# Delete the remote copy of the `my-feature` branch from the origin. The `:`
# prefix sends this through as a "delete" command for the given branch.
git push origin :my-feature
```

### I want to update `master` because my `push` was rejected.

If you've committed changes to `master` but you forgot to `pull` recent changes from the remote `master` branch, your next `push` will be rejected with an error that looks like, _"Updates were rejected because the tip of your current branch is behind its remote counterpart"_. To fix this, you can use the `--rebase` modifier:

```sh
git checkout master
git merge --no-ff my-feature

# Oh noes! You forgot to pull in the latest remote copy of `master` before you
# merged your `my-feature` commits. No problem, just `--rebase` your local
# `master` on the remote branch. This will move your local changes to the tip
# of the `master` branch.
git pull --rebase 

# Now that you've pulled-in the remote changes, you should be able to push
# your updated `master` branch.
git push origin master
```

### I want to remove a file from my staging area.

If you accidentally added too many files to the staging area (in preparation for a `git commit`), you can use the `rm --cached` command to remove them from the staging area but keep them in the working tree:

```sh
git add .

# Oh noes! You didn't mean to add all of the files to the staging area. You
# can remove some of the staged files using the `--cached` modifier:
git rm --cached secrets.config
```

If you accidentally added an entire directory to the staging area, you can add the `-r` modifier to recursively apply the `rm` command:

```sh
git add .

# Oh noes! You didn't mean to add the ./config directory. You can recursively
# remove it with the `-r` modifier:
git rm --cached -r config/.
```

When you `rm` files using `--cached`, they will remain in your working tree and will become "unstaged" changes.

### I want to squash several commits into one (or more) commits.

Your commit history is a representation or your personality. It is a manifestation of your self-respect and the respect you have for your team. As such, you will often need to rewrite your feature branch's history before merging it into `master`. This allows you to get rid of intermediary commit messages like, _"still working on it."_ and _"Meh, missed a bug."_. To do this, you can perform an "interactive rebase".

The "interactive rebase" gives you an opportunity to indicate how intermediary commits should be rearranged. Some commits can be "squashed" (combined) together. Others can omitted (remove). And others can be edited. When performing an interactive rebase, you have to tell `git` which commit to use as the starting point. If you're on an up-to-date feature branch, the starting point _should be_ `master`.

```sh
# Create the `my-feature` branch based on `master`.
git checkout master
git checkout -b my-feature

# ... changes to the working tree (your file system).
git add .
git commit -m "Getting close."

# ... changes to the working tree (your file system).
git add .
git commit -m "Missed a bug."

# ... changes to the working tree (your file system).
git add .
git commit -m "Uggggg! Why is this so hard?"

# ... changes to the working tree (your file system).
git add .
git commit -m "Woot, finally got this working."

# At this point, your commit history is sloppy and would bring much shame on
# your family if it ended-up in `master`. As such, you need to squash the
# commits down into a single commit using an interactive rebase. Here, you're
# telling `git` to use the `master` commit as the starting point:
git rebase -i master
```

As this point, `git` will open up an editor that outlines the various commits and asks you how you want to rearrange them. It should look something like this, with the commits listed in ascending order (oldest first):

```sh
pick 27fb3d2 Getting close.
pick e8214df Missed a bug.
pick ce5ed14 Uggggg! Why is this so hard?
pick f7ee6ab Woot, finally got this working.

# Rebase b0fced..f7ee6ab onto b0fced (4 commands)
#
# Commands:
# p, pick = use commit
# r, reword = use commit, but edit the commit message
# e, edit = use commit, but stop for amending
# s, squash = use commit, but meld into previous commit
# f, fixup = like "squash", but discard this commit's log message
# x, exec = run command (the rest of the line) using shell
# d, drop = remove commit
```

At this point, you can identify the later commits as needing to be squashed (`s`) down into the oldest commit (the one you are `pick`ing):

```sh
pick 27fb3d2 Getting close.
s e8214df Missed a bug.
s ce5ed14 Uggggg! Why is this so hard?
s f7ee6ab Woot, finally got this working.
```

Once saved, `git` will prompt you to provide a cleaner commit message. And, once provided, your four shameful commits will be squashed down into a single, cohesive, meaningful commit.

### I want to squash several commits into one commit without using `rebase`.

In the vast majority of cases, if your `git` workflow is clean and true and your feature branch is short-lived, an interactive rebase should be straightforward and pain-free. However, once you _make the mistake_ of periodically merging `master` into your feature branch, you are inviting a world of hurt. In such a case, you can use the `merge` command with the `--squash` modifier as an escape hatch.

When you run `git merge --squash`, you copy the file-changes from one branch into another branch without actually copying the commit meta-data. Instead, the changes are brought-over as _staged changes_ on top of the current branch. At that point, you can commit all the staged changes as a single commit.

Assuming your `my-feature` branch needs to be "fixed", you can use the following workflow:

```sh
# Assuming that the `my-feature` branch is the branch that needs to be fixed,
# start off my renaming the branch as a backup (the `-m` modifier performs a
# rename):
git checkout my-feature
git branch -m my-feature-backup

# Now, checkout the `master` branch and use it to create a new, clean
# `my-feature` branch starting point.
git checkout master
git checkout -b my-feature

# At this point, your `my-feature` branch and your `master` branch should be
# identical. Now, you can "squash merge" your old feature branch into the new
# and clean `my-feature` branch:
git merge --squash my-feature-backup

# All the file-changes should now be in the `my-feature` branch as staged
# edits ready to be committed.
git commit -m "This feature is done and awesome."

# Delete the old backup branch as it is no longer needed. You will have to
# force delete (`-D`) it since it was never merged into `master`.
git branch -D my-feature-backup
```

> **ASIDE**: You should almost never need to do this. If you find yourself having to do this a lot; or, you find yourself dealing with a lot of "conflict resolution", you need to reevaluate your `git` workflow. Chances are, your feature branches are living way too long.

### I want to temporarily set-aside my feature work.

The life of a developer is typically "interrupt driven". As such, there is often a need to briefly set aside your current work in order to attend to more pressing matters. In such a case, it is _tempting_ to use `git stash` and `git stash pop` to store pending changes. But, _do not do this_. Stashing code requires unnecessary mental overhead. Instead, simply commit the changes to your current feature branch and then perform an interactive rebase later on in order to clean up your commits:

```sh
# Oh noes! Something urgent just came up - commit your changes to your feature
# branch and then go attend to the more pressing work.
git add .
git commit -m "Saving current work - jumping to more urgent matters."

git checkout master
```

Now, you never have to remember where those pending changes are. This guarantees that you won't lose your work.

If you were working directly on `master` when urgent matters came up, you can still avoid having to use `git stash`. To keep your work, simply checkout a new branch and the commit your pending changes to that new branch:

```sh
# Oh noes! Something urgent just came up - checkout a new branch. This will
# move all of your current work (staged and unstaged) over to the new branch.
git checkout -b temp-work

# Commit any unstaged changes.
git add .
git commit -m "Saving current work - jumping to more urgent matters."

git checkout master
```

Now, your `master` branch should be back in a pristine state and your `temp-work` branch can be continued later.

### I want to keep my changes during conflict resolution.

If your Git workflow is healthy - meaning that you have short-lived feature branches - conflicts should be very few and far between. In fact, I would assert that getting caught-up in frequent conflicts is an indication that something more fundamental to your workflow is primed for optimization.

That said, conflicts do happen. And, if you want to resolve a conflict by selecting "your version" of a file, you can use `git checkout --theirs` in a `merge` conflict, a `cherry-pick` conflict, and a `rebase` conflict.

In a `merge` conflict, `--theirs` indicates the branch being merged into the current context:

```sh
git checkout master
git merge --no-ff my-feature

# Oh noes! There is a conflict in "code.js". To keep your version of the
# code.js file, you can check-it-out using --theirs and the file path:
git checkout --theirs code.js
git add .
git merge --continue
```

Similarly, in a `cherry-pick` conflict, `--theirs` indicates the branch being cherry-picked into the current context:

```sh
git checkout master
git cherry-pick --no-ff my-feature

# Oh noes! There is a conflict in "code.js". To keep your version of the
# code.js file, you can check-it-out using --theirs and the file path:
git checkout --theirs code.js
git add .
git merge --continue
```

In a `rebase` conflict, `--theirs` indicates the branch that is being _replayed_ on top of the current context (**See Aside**):

```sh
git checkout my-feature
git rebase master

# Oh noes! There is a conflict in "code.js". To keep your version of the
# code.js file, you can check-it-out using --theirs and the file path:
git checkout --theirs code.js
git add .
git rebase --continue
```

> **ASIDE**: Using `--theirs` in a `rebase` can seem confusing because you are already in "your" feature branch. As such, it would seem logical that your version of the code would be targeted with `--ours`, not `--theirs`. However, a `rebase` operates _kind of like_ a series of `cherry-pick` operations. You can think of a `rebase` as doing the following:
> 
> * Check-out an earlier, common commit between your feature branch and the target branch.
> * Cherry-pick your feature branch commits onto the earlier commit.
> * Replace your feature branch with this temporary branch
> 
> With this mental model, "your" version - targeted using `--theirs` - is the version being cherry-picked into the "current context" (the temporary branch).

### I want to find the commit that deleted a file.

To find a deleted file, you can use the `git log` command and filter the results based on file status and path patterns. In this case, you want to use `--diff-filter=D` which limits the results to deleted files. And, since the files in question have been deleted, the path pattern must come after the final `--` delimiter:

```sh
# Find the commit that deleted the file "projects.js".
git log --diff-filter=D --name-only -- wwwroot/app/projects.js
```

The `--name-only` option includes statistics about the commit (which files were changed); but, limits the file meta-data to include file paths only.

Of course, since you are looking for a _delete file_, you may not remember the exact file path of the deleted file. In that case, you can use pattern matching on the file path:

```sh
# Find the commit that deleted the file "projects.js" that resided somewhere
# in the "app" directory. The double-asterisk matches across directories.
git log --diff-filter=D --name-only -- "wwwroot/app**/projects.js"

# You can even use pattern matching on the file name itself if you can't
# remember exactly what it was named.
git log --diff-filter=D --name-only -- "wwwroot/**/*project*.js"
```

The default output of the `git log` command can be a bit verbose since it outputs the commit message along with the deleted files. To minify the output, you can use the `--oneline` and `--pretty` options:

```sh
# Find the commit that deleted the file "projects.js", but only show a one-line
# commit message and the list of files.
git log --diff-filter=D --name-only --oneline -- "wwwroot/app**/projects.js"

# To get slightly easier-to-read output, you can use the `--pretty` option with
# some specialized formatting (instead of the `--oneline` option). This
# includes the abbreviated hash, the author, the relative date, and the
# subject line. And, includes some human-friendly line-breaks.
git log --diff-filter=D --name-only --pretty=format:"%Cgreen%h - %an, %ar : %s" -- "wwwroot/app**/projects.js"
```

### I want to find the commit that deleted a file that contained a piece of code.

To find a deleted file that contained a given piece of code, you can use the `git log` command and filter based on pattern matching within the diff. In this case, you want to use `--diff-filter=D` which limits the results to deleted files.

You can use the `-S` option to match on a string literal:

```sh
# Find the commit that deleted a file that contained the code 'isProcessed'.
git log -S 'isProcessed' --diff-filter=D --name-only

# To limit the search to the "app" directory, you can include a file path after
# the final `--` delimiter.
git log -S 'isProcessed' --diff-filter=D --name-only -- wwwroot/app/

# To make the search case-insensitive, include the -i option.
git log -S 'isprocessed' -i --diff-filter=D --name-only
```

You can use the `-G` option to match on a Regular Expression pattern instead of a string literal:

```sh
# Find the commit that deleted a file that contained the code `isProcessed`,
# matching on strict word-boundaries.
git log -G '\bisProcessed\b' --diff-filter=D --name-only

# To make the search case-insensitive, include the `-i` option.
git log -G '\bisprocessed\b' -i --diff-filter=D --name-only
```

The default output of the `git log` command can be a bit verbose since it outputs the commit message along with the deleted files. To minify the output, you can use the `--oneline` and `--pretty` options:

```sh
# Find the commit that deleted a file that contained the code `isProcessed`,
# matching on strict word-boundaries.
git log -G '\bisProcessed\b' --diff-filter=D --name-only --oneline

# To get slightly easier-to-read output, you can use the `--pretty` option with
# some specialized formatting (instead of the `--oneline` option). This
# includes the abbreviated hash, the author, the relative date, and the
# subject line. And, includes some human-friendly line-breaks.
git log -G '\bisProcessed\b' --diff-filter=D --name-only --pretty=format:"%Cgreen%h - %an, %ar : %s"
```

Once you locate the commit that appears to contain your code, you can use the `git show` command to view the contents of the commit delta:

```sh
# Find the commit that deleted a file that contained the code `isProcessed`,
# matching on strict word-boundaries.
git log -G '\bisProcessed\b' --diff-filter=D --name-only --oneline

# The above `log` action listed commit `aef037`. Use `git show` to output the
# changes made in the given commit.
git show aef037
```
