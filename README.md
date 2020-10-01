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


