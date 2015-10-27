# Working in team with git

When your are working on a project in a team, sharing your code is quickly a problem. You can use USB key, email or cloud folders, but each time two peaple have edited the same file, this is a nightmare. Git is the best solution to handle this problem. It also give you a lot of feature INDISPENSABLE for professional programming.

## What is Git ?

Git in a Vesion Control System (CVS). Its job is to save every small change in your code.


....





## The basis

### Installation

Mac : `brew install git`
Ubuntu: `sudo apt-get install git`

### Your first commit

The first thing you need to do, is to create a new versioned project. The simplest way to do is to clone an existing repository on [github](http://www.github.com).
Create a new account and on your profile page, click on the button "New Repository". Give it a name and a README. You have now your first repository ready.

To make copy on your computer, open a terminal and write :
```bash
git clone git@github.com:your-username/your-repo-name.git
```
You can find the right url in a little input in the right column of your project homepage.

If everything worked fine, you have now a new you folder with the content of your repository in. Let's try to change something in.
```bash
cd your-project-name
echo "## Author\nThe Awesome `whoami`" >> README.md
```
To save this change and share it with the others, you need to make a new commit.
A commit is a new version of your application. It save the change you made until the last one.

The first thing to do, is to choose what files we want to save in the next commit. It could be done with the `add` command :
```bash
git add [--verbose | -v] [<pathspec>...]
```

In our case, we just want to add the README.md :
```bash
git add README.md
```

To see waht files have been modified and what file have been added you can use :
```bash
git status
```

```bash
git commit [-m <msg>]
```
