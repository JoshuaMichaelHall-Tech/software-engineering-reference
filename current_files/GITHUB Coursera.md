Local - Project Directory
- working tree - files being edited 
- staging area - files ready to commit
- local repository - commits
Remote
- remote repository

Initialize a project:
```Term
# From within new project directory:
git init
```

View status of files in working tree and staging areas:
```Term
git status
```

Add content to staging area:
```Term
# Staged content is part of the next commit.
git add <file.txt | directory>
```

Add all untracked or modified content to staging area:
```Term
git add .
```

Remove content from staging area:
```Term
git rm --cached <file.txt | directory>
```

Add staged content to local repository:
```Term
git commit
#Add optional message
git commit -m "Message"
```

View commit history:
```Term
git log [--oneline] [-2(view only 2 most recent commits)]
```

`clone` a remote repository when there is no local repository.
`add` a remote repository when there is a local repository.

Clone a remote repository:
```Term
git clone <url/to/projectname.git> [localprojectname]
```

Display info about remote repository:
```Term
git remote [--verbose | -v]
```

`origin` is now an alias for url to remote repository.

Add a remote repository:
```Term
git remote add [name, e.g. origin] <url/to/projectname.git>
```

`git push` writes commits for a branch to a remote repository.

Pushing local commits to remote:
```Term
git push [-u] [<url | name>] [<source_branch>]
```

Add file to staging area:
```Term
git add <filename>
```

Commit to local repository:
```Term
git commit [-m "Message"]
```

Push commit to local repository:
```Term
git push origin main
```

View local repository's commit history:
```Term
git log --oneline [--graph] [--all]
```

`HEAD -> main`
`HEAD` is a reference to the current commit.
The content of that commit is in your working tree. `main` is the name of the branch, and this commit is the tip of the branch, so this is the `main` branch label. The arrow represents that the `HEAD` reference points to the `main` branch label, which points to the SHA-1 of the commit.

Show contents of last commit object:
```Term
git show <(min first 4 chars of ID/SHA=1 | HEAD | main)>
(~ refers to parent. ~~, ~2 refer to grandparent)
(^ refers to parent. ^^, ^2 refer to parent of parent)
```

Tag a commit:
```Term
# -a to annotate
# -m for message
git tag -a -m "message" v1.0 # tags locally
git push origin v1.0 # tags remotely
```

View a tag:
```Term
git tag # view local tags
git show v1.0
```

Create a branch:
```Term
# list branches
git branch 

# two command approach
$ git branch featureX
$ git checkout featureX

# one command approach
$ git checkout -b featureX
```

Checkout a branch:
```Term
git checkout <name>
```

Delete a branch:
```Term
git branch -d <name> # If no commits
git branch -D <name> # Will leave dangling commits, auto deleted later

# recover dangling commits
git reflog # view history
git checkout -b <name> [SHA-1] 
```

Merge another branch into current:
```Term
git merge <other_branch> # Tries to fast forward, then merge-commit
git merge --no-ff <other_branch> # Forces merge-commit
# Should consider deleting other branch
```

