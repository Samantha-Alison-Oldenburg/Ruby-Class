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


**That's it, you're done with your first homework!**
