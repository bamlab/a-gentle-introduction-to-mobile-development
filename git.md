# Working in team with git

When your are working on a project with a team, sharing your code can quickly become a problem. You can use USB drives, emails or cloud folders. But every time two people edit the same file, it becomes a nightmare. Git is the best solution to handle this problem.
It also gives you a lot of vital features for professional programming.

## What is Git ?

Git in a Vesion Control System (CVS). Its job is to save every small change in your code.
Every change is saved in a new revision of the application. A version contains a verison number, the author of the change and the date.

Git allows you to go switch between revision, merge two diferents, go back in the history of your application, set label, ...


give example ...




## The basics

### Installation

Mac : `brew install git`
Ubuntu: `sudo apt-get install git`

### Your first commit

The first thing you need to do is to create a new versioned project. The simplest way to do so is to clone an existing repository on [github](http://www.github.com).
Create a new account and on your profile page, click on the button "New Repository". Give it a name and a README. You now have your first repository ready.

To make a copy on your computer, open a terminal and write:
```bash
git clone git@github.com:your-username/your-repo-name.git
```
You can find the right url in a little input in the top of your project homepage.

If everything worked fine, you now have a new folder containing the content of your repository. Let's try to change something in.
```bash
cd your-project-name
echo "## Author\nThe Awesome `whoami`" >> README.md
```
To save this change and share it with others, you need to make a new commit.
A commit is a new version of your application. It saves the change you made until the last one.

The first thing to do, is to choose what files we want to save in the next commit. It could be done with the `add` command:
```bash
git add [--verbose | -v] [<pathspec>...]
```

In our case, we just want to add the README.md:
```bash
git add README.md
```

To see which files have been modified and which file have been added you can use:
```bash
git status
```

```bash
git commit [-m <msg>]
```
