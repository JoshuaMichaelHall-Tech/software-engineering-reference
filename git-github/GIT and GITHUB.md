LS Book Summaries:
https://launchschool.com/books/git/read/summary

# List of key git commands:

- `git add .` — Stage your files, preparing them for the next commit.
- `git commit -m 'your message here'` — Commit your changes, creating a snapshot of your code.
- `git checkout -b development` — Creates a new `development` branch and switches to it. This is shorthand for the following two commands.
- `git branch development` — Creates a new branch called `development`.
- `git checkout development` — Switches you over to the `development` branch.
- `git checkout main (or master)` — Switch back to the `main/master` branch.
- `git merge development` — Merge the changes from `development` to the current branch.
- `git branch -d development` — Delete the `development` branch.
- `git branch -D development` — Force delete the `development` branch.
- `git status` — Shows you the status of your current branch.
- `git log` — View the repository's commit history.

SCM Source Control Management

SCM Workflow - SCM tools keep a historical record of the files in your codebase, as well as manage **SCM workflows** that allow large teams to work on large, complex codebases with hundreds or thousands of files.

SCM tools, like git, store your files in a **repository**, or **repo** for short.

Git is different from some other SCM tools because it is distributed, meaning there is no central code repository.

Git is considered a **distributed version control system**, or **dvcs**. In practice, however, most development teams that use git will not push commits directly to each other. Instead, they rely on a central repository to act as the main repo, and that main repo is typically hosted on [github.com](https://github.com/).

``` 
git --version
sudo apt-get update
sudo apt-get install gitk
```

**Create Example Project**
```
mkdir git_basics 
cd git_basics 
echo '# README #' > README.md 
echo '# LICENSE #' > LICENSE.md
```

**git init**
```
#Set default to main...
git config --global init.defaultBranch main

#initialize git
git init
```

**Remove git init**
 If you've accidentally typed that command in a directory that you didn't want to turn into a git repository, all you have to do is delete the `.git` directory within that directory.

**Set git identity**
```
git config --global user.name "Joshua Michael Hall"
git config --global user.email "SEJoshuaHall@gmail.com"
```

**git ignore**
create .gitignore file and add list of files to ignore in the file
```
touch .gitignore

#In .gitignore file, add:
db/*.sqlite3
```

**Keep in mind that once you upload sensitive or private data to a public repo, there is no way to remove it entirely. Your only options are to either delete the entire repo or make the repo private.**

**git status**
```
git status
```

**track files**
```
git add <file>
```

The output from `git status` is showing us what's called our **working tree** and **staging area**. As we saw in the output above, we have new files in our working tree that we'd like to **commit** to our repo.

**git commit**
```
git commit -m 'Add first project files'
```
The -m flag allows you to add a message, which is best practice.

**git log**
To review git activity, use
```
git log
```

In some teams, **commit hygiene** is highly regarded so it's important to make sure each commit contains a logical grouping of changes (eg, a bug fix or a feature) with a clear commit message. When anyone issues `git log` on the repository, a clear historical list of commits appears.

**Branching**
To create a branch, we **fork** it from another existing branch. We can **merge** commits from the experimental branch into our `main` branch (and then delete the experimental branch, if we want to). It's important to note that only commits, not staged files, are forked and merged. In git, we only move **commits** around.

**Tracking**
You can set up your local branches to `track` remote branches, which means they will automatically push code to and pull code from the tracked branch on the remote repository.

**Connect to Remote Repo**
```
# Substitute your GitHub username and your repo name where indicated 
git remote add origin https://github.com/GITHUBUSERNAME/REPONAME.git
```

**git push**
```
git push -u origin main
```

**git pull**
The first thing we need to do is **fetch** the repo, which will download the commit data for each branch that the remote repo contains.
```
git fetch
```
The next thing we need to do is look at what has changed.
```
#Compare modified remote repo to unmodified local
git diff main origin/main
#Compare unmodified remote repo to modified local
git diff origin/main main
```
Once you're sure that you want to pull the changes into your local repo, type:
```terminal
git pull --ff-only
```
`git pull --ff-only` combines `git fetch` and `git merge --ff-only` into one command.

**git clone**
```
git clone <remote repository url> <local directory name>
```
`git clone` is used mainly when you need to work with a remote repository, and do not yet have a local repository created.

|Command|                                            When To Use|
|`git init`|                                             Create a new local repository.|
|`git remote add origin REMOTEURL`|     Add an existing remote repo as a remote of existing local repo.|
|`git clone REMOTEURL`|                          Pull down contents of existing remote repo into a new local repo, and add a remote to the local repo pointing to remote repo.|

