# Working in team with git

When your are working on a project with a team, sharing your code can quickly become a problem. You can use USB drives, emails or cloud folders. But every time two people edit the same file, it becomes a nightmare. Git is the best solution to handle this problem.
It also gives you a lot of vital features for professional programming.

## What is Git ?

Git is a Version Control System (VCS). Its job is to save every small change in your code.
Every change is saved in a new revision of the application. A version contains a version number, the author of the change and the date.

Git allows you to go switch between revision, merge two different, go back in the history of your application, set label, ...

For example, you can make changes at a revision 1 to create a revision 2. At any moment, you can go back to revision 1. If another member of you team create a revision 2b from the revision 1, you can merge it with your revision 2. You will create a version 3 which contains the change in revision 2 and 2b.

## The basics

### Installation

Mac: `brew install git`
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
A commit is a new version of your application. It contains the changes made since the last commit.

The first thing to do, is to choose what files we want to save in the next commit. It can be done with the `add` command:
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
Then, you can create the commit:
```bash
git commit [-m <msg>]
```

### Sharing with people

Your first commit have been created, but you didn't send your changes to your teammate. To do so, you need to "push" your changes on the server.
```bash
git push
```
Now, you should see your commit on the github interface.

The reverse command of `push` is `pull`.  If someone made change and pushed them to the server and you want get it, you'll need to use the command:
```bash
git pull
```
Try it after editing a file in the github interface.


One condition must be fulfilled to push to the server repository. You can push only if you have the same commits as the server with some more.
If you try to push a commit and someone else just did the same, you will have an error. The reason is, there is a commit on the server than you don't have on your local machine.

The only way to push your commit is to pull first. Git will merge your local changes with the remote ones. A new commit will be created to regroup everything.
Now you can push without problem.

### Resolving Conflicts

The way `git` merge all the changes is very smart. But there is a situation that it cannot resolve alone. It happen when you and your teammate have changed the same line of the same file. Git cannot choose what modification it need to take and will create a conflict.

```bash
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

You need now to resolve manually all the conflict. To do so, you can use the following command:
```bash
git mergetool
```

This command should open a software to help you to resolve the conflict. If you don't have one, I recommend you to install `opendiff` for MACOS or `meld` for Ubuntu.

### Using Branches 

One of the most powerful tool to git is the branch system. A branch is like a copy of your project. The default one is named `master`.

Let's create a new branch: 
```bash
$ git checkout -b "my-new-branch"
```

Now you have 2 branches and you have switched to the `my-new-branch` branch:
```bash
$ git branch
  master
* my-new-branch
```

Now everything happen as if you have 2 folder with two copy of your project. You can make any change in `my-new-branch` without affecting the master branch.

For example if we create a new commit:
```
echo "Made in a new branch" >> README.md
git add README.md
git commit -m "A commit made in the my-new-branch branch"
```

We can see it with `git log`: 
```bash
$ git log --oneline
9133367 A commit made in the my-new-branch branch
5d77249 Initial commit
```

But if I switch to the `master` branch:
```bash
$ git checkout master
$ git branch
* master
  my-new-branch
```

I don't see my commit anymore:
```bash
$ git log --oneline | cat
5d77249 Initial commit
```

When you have finished your work in a new branch, you can merge it with the rest of the code with `git merge`. The command will create a new commit if needed. Let's see an example: 

After the previous steps, I have two commit on `my-new-branch` and one commit in master. I create a new commit in master:
```
git co master
echo "console.log('foobar');" >> newFile.js
git add newFile.js
git commit -m "Adding the newFile script"
```

I can now see it:
```bash
$ git log --oneline
187632d Adding the newFile script
5d77249 Initial commit
```

Now I merge the other branch:
```bash
$ git merge my-new-branch
Merge made by the 'recursive' strategy.
 README.md | 1 +
 1 file changed, 1 insertion(+)
```

I can see a summary of what happened with `git log --graph`.
```bash
$ git log --graph --oneline
*   6882170 Merge branch 'my-new-branch'
|\
| * 9133367 A commit made in the my-new-branch branch
* | 187632d Adding the newFile script
|/
* 5d77249 Initial commit
```


