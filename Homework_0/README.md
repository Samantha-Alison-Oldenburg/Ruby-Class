# Homework 0: GitHub and Git #

## Background ##

GitHub and git are tools that programmers use invariably.

Git is basically google docs for code, but almost one and a half decades old. It allows for you to have a copy of code on your machine that you can make changes to. You can then "push" those changes to a central location shared by many people. Unlike Google Docs, you get to choose what to save to the shared location, and when it should be saved.

GitHub is a place where people can store those central code locations (called repositories). It's also a great way to share completed code with other people.

## Requirements ##
* Ubuntu Machine

## 1. Setup git ##


1. Open the `Terminal` app in Ubuntu
2. Type the following command into the terminal:

```
git
```

3. If you get something like below, you're good to go!

```
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]
```

4. If you get something like `command not found` enter the following into the terminal:

```
sudo apt-get install git
```

## 2. Cloning this code repository ##

Cloning a repository means downloading the code to your computer and setting up the folder it is downloaded in to be able to make changes and push them.

1. Make a folder to store your cloned repositories, then move to that folder. In the terminal:

```
# The semicolon allows you to do two commands on one line.
mkdir ~/Workspace; cd ~/Workspace
```

2. Clone this repository. It will create a folder named `ruby-class` in `~/Workspace`:

```
git clone https://github.com/Samantha-Alison-Oldenburg/ruby-class.git
```

## 3. Git Branching ##

Git repositories are like trees, made of branches. They have a main branch, or trunk (often called the `master` branch). The master branch is the state of the code a user would download and use. They also have branches that diverge from that master branch. Most coding tasks in the real world involve creating a branch off of master, putting your changes into that branch, and then merging your branch back into master once you're done with your task.

### Why branching? ###
* Be able to push up changes even if your task isn't complete.
  * No half done tasks in master
* Make changes to the code that people can see without changing the master branch
  * I'll be able to see your work while keeping the templates I make for you unchanged. You'll see some of these templates in the next homework.
* A lot more reasons (trust me)

### Making your own branch ###
1. Go to your local copy of the repository.

```
cd ~/Workspace/ruby-class
```

2. Create a branch for your homework assignments.

```
git branch -b {your_name_goes_here}_homework_assignments
```

git checkout 'checks out' a branch. Think of it like checking out a book at a library. The `-c` means "I'm creating a new branch that doesn't exist on the remote". The remote is the central code location.

3. Open this file in a text editor of your choice. Ubuntu machines should have gedit so I'll use that: `gedit ~/Workspace/ruby-class/Homework_0/README.md`

4. Add stuff to the file. Remove stuff. Make changes! Don't forget to save.

5. Make a commit. A commit is a group of changes you want to create together
  a. Stage the changes you made for the commit
```
git add ~/Workspace/ruby-class/Homework_0/README.md
```

  b. Create the commit. The `-m` lets you specify your commit message: "My first commit"

```
git commit -m "My first commit"
```

6. Push your commit: `git push`

7. Oops. That didn't work, because your branch doesn't exist in the remote yet. Let's add that branch in when we push.

``` bash
git push --set-upstream origin {the branch name you created above}
```

`origin` is the default name of the remote you got by cloning.

**That's it, you're done with your first homework!**
