# Welcome 

In this workshop we're going to be learning the basics of using git and GitHub.

## What is git? 
Git is a distributed version control system that allows us to make changes to 
a git repository locally, and then send our patches and changesets to others and 
automatically manage the changes so that we can work together on projects.

## What is GitHub? 
GitHub is a hosting service for git repositories. You can post your code on GitHub 
and using it to collaborate with people on projects.

## Cloning a Repository
To start, we're going to clone this repository. This means we're going to download 
all of the source code from the repo on GitHub to a local version of it. 

Open up your command line and run
```
$ git clone https://github.com/nixin72/git-workshop.git
```

Then, we're going to move into that directory, and delete the `.git` directory

```
$ cd git-workshop
$ rm -rf .git
```

**NOTE:** Normally we wouldn't do this when cloning a git repo, but we're going to this time 
so that you can start a new repo from scratch.

## Initializing a repository
To get started with git, we need to initialize our project as a git repository.
To do this, we're going to run the command `git init`.

What this will do, is it'll create a `.git` directory that contains a bunch of information
about the current directory. Don't worry about it for now. 

Now that our current directory is a git repo, how do we get our changes on to GitHub so that 
we can work with others on it?

## Staging local changes
The first thing we're going to do is stage our local changes. What this means is we're going
to give git a list of files that we've made changes to, and tell git that we'd like to add
these changes to our staging. 

So we can do
```
$ git add README.md
```
And that will add the README.md file to our staged changes. We use these staged changes to 
prepare all of the stuff that we eventually want to be commited. 

## Commiting staged changes. 
Once we have our changes staged, then we can commit them. What this will do, is it will add
to our git history all of the changes that we made in this set of staged files. Git will 
be able to keep track of the history of all of our commits so that we can rollback our
history at any point to any given commit. 

To commit our changes, we do
```
$ git commit
```
This will open up our default system text editor to write a commit message.
If you want to just write the message on the command line, we can do

```
$ git commit -m "My commit message"
```

## Getting the changes onto GitHub
So, before we can push the changes to GitHub, we first need to go onto GitHub and create a 
remote repository. So open up your browser and log into your GitHub account. In the top-right
hand corner, there's a little plus. Click that, and the first option in the dropdown is to 
create a new repository. Give the repository a name, then click "Create Repository". For now, 
don't click any of the checkboxes. 

Once you've clicked the "Create Repository", GitHub will bring you to a page for a new empty
repository. We're going to use this empty repo to push our local changes into. 

Copy the name for the repository, it'll be the first line under the "Quick Setup" heading. 
It should look something like https://github.com/yourusername/repo-name.git. Copy that.

Then, back in your command line, run the command 
```
$ git remote add origin https://github.com/yourusername/repo-name.git
```
Now, git will have the variable `origin` that points to that remote repository whenever we 
want to push to our remote repo. So now that we have our remote added, we can run the 
command 

```
$ git push origin master
```

And this will take all the local changes we've made, and push them to the master branch at 
that remote repository that we have on GitHub.

---

When working on projects on your own, most of the time these are all you're going to need
to work with git and GitHub. However, we use git to work in teams and work on big projects
collaboratively. To be able to do that effectively, we'll need to know a bit more. 

---


## Conclusion
I hope you've learned a lot about how to use git for your team projects! If you learned from
the workshop, let me know on Discord. If not, write an issue on the GitHub repo for this and
let me know what I can improve. 

## Appendix
Here's all the commands that we learned to use in this tutorial:

### git clone
#### Example
```
$ git clone https://github.com/username/repo-name.git
```
#### Description
Will clone a remote git repository to a local directory

### git init
#### Example
```
$ git init
```
#### Description
Will initialize the current directory as a new git repo. If it's already a git repo, it'll fail.

### git add
#### Example
```
$ git add filename.txt
$ git add -p filename.txt
```
#### Description
Will stage all the changes in that file to be commited.
With the `-p` flag supplied, you can pick only the changes you want to be commited.

### git commit
#### Example
```
$ git commit -m "my commit message"
```
#### Description
Will add all the changes staged to a "commit" so that we can use that as kind of a checkpoint 
or rollback point in our git history.

### git push
#### Example
```
$ git push -u origin master
```
#### Description
Will push all of our commited changes on the current branch to the remote branch.

### git pull
#### Example
```
$ git pull origin master
```
#### Description
Will pull all of the changes in the remote repository into our local repository on the current
branch. If there's merge errors, you'll need to fix them.

### git fetch
#### Example
```
$ git fetch origin
```
#### Description
Will allow you to fetch all the objects on the remote branch and bring them into your local.

### git status
#### Example
```
$ git status
```
#### Description
Will show you all of the changes that have been made locally up to this point that haven't been
commited. Will show you all files created/modified/deleted, staged changes, etc.

### git diff
#### Example
```
$ git diff filename.txt
```
#### Description
Will show you all the differences in `filename.txt` between the current local changes and what 
the file looked like in the most recent commit.

### git checkout
#### Example
```
$ git checkout master
$ git checkout -b my-new-branch-name
```
#### Description
Will checkout a branch and change all of your local files to the most recent commit on that branch.
If the -b flag is supplied, it'll create the new branch will all your current changes.

### git branch
#### Example
```
$ git branch -l
$ git branch -d branch-name
```
#### Description
Will allow you to list all branches or delete a specified branch

### git stash
#### Example
```
$ git stash
$ git stash pop
$ git stash clear
```
#### Description
Allows you to stash changes quickly if you want to change branches or check something out 
without adding those changes to a commit. 
Adding the `pop` subcommand will pop all of the changes out of the stash and apply them
against your current files. 
Adding the `clear` subcommand will clear the stash of all the changes that have been added
to it.

### git remote
#### Example
```
$ git remote add origin https://github.com/username/repo-name.git
$ git remote remove origin
```
#### Description
Adds or removes remote repositories that you can use to collaborate with people. 
Can have multiple remote repositories so you can do things like push to either GitHub or
Heroku.

### git reset
#### Example
```
$ git reset HEAD~1
```
#### Description
Allows you to undo things that you messed up. The example above will undo the most 
recent commit if you did something you didn't want to do.
