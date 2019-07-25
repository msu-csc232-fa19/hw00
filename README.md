# hw00

This non-graded assignment is used just to get students linked into the CSC232 GitHub Classroom managed by Jim Daehn.

_As suggested in the previous sentence, this is a non-graded assignment. Whether you choose to work on this or not is your perrogative. The end-goal of this assignment is to simply link you to my GitHub classroom. This will happen simply by virtue of you following the assignment link provided to you by your instructor._

## Goals

Upon completion of this assignment, the student will have learned to

* accept a GitHub Education assignment
* clone a repository from GitHub
* create a development branch within in which to do their work
* create a pull request to complete an assignment

## Prerequisites

Before a student can proceed with this assignment, the student must have

* signed up for a GitHub account
* installed `git` on their computer

If you use a Windows machine, `git` is easily installed by downloading `git` for Windows here: [https://gitforwindows.org/](https://gitforwindows.org/). There are many alternatives, but this is a very common one and mirrors a program installed on our lab machines. All `git` commands presented in this README are executed, for example, in the `Git Bash` console window.

Furthermore, you'll want to check out these videos hosted on YouTube. The following were located by simply searching for "GitHub & Git Foundations" on YouTube.

* [What is GitHub?](https://www.youtube.com/watch?time_continue=8&v=w3jLJU7DT5E) (3:45)
* [GitHub Training & Guides](https://www.youtube.com/user/GitHubGuides)
  * Getting Started/Setup
    * [Intro](https://www.youtube.com/watch?v=FyfwLX4HAxM&list=PLDx-eoZGKRiH1S5l82vzLtoiuKqTLH9yN) (4:04)
    * [Setup](https://www.youtube.com/watch?v=7Inc0G0wutk&list=PLKtIksTx7tTpxy5Gw7itc0zdgZtaLHWW0) (2:15)
    * [Config](https://www.youtube.com/watch?v=ZChtKFLiaNw) (2:48)
  * Fundamentals (Operations we'll use most often)
    * [Branch](https://www.youtube.com/watch?v=H5GJfcp3p4Q) (2:25)
    * [Checkout](https://www.youtube.com/watch?v=HwrPhOp6-aM) (3:11)
    * [Commit](https://www.youtube.com/watch?v=A-Cll9jEnnM) (4:08)
    * [Pull Requests](https://www.youtube.com/watch?v=d5wpJ5VimSU) (4:26)
    * [Merge](https://www.youtube.com/watch?v=yyLiplDQtf0) (4:50)
    * [GUI](https://www.youtube.com/watch?v=BMYOs5jflGE) (3:47)
  * Additional, useful operations
    * [Ignore](https://www.youtube.com/watch?v=4VBG9FlyiOw&t=6s) (3:06)
    * [Diff](https://www.youtube.com/watch?v=RXSriVcoI70) (3:33)
    * [Log](https://www.youtube.com/watch?v=Ew8HQsFyVHo) (4:57)
    * [Rebase](https://www.youtube.com/watch?v=SxzjZtJwOgo&frags=pl%2Cwn) (4:20)
    * [Remove](https://www.youtube.com/watch?v=jtuHOIlfS2Q) (3:30)
    * [Move](https://www.youtube.com/watch?v=ipdgyfPq8FE) (5:16)
* [Git and GitHub Crash Course For Beginners](https://www.youtube.com/watch?v=SWYqp7iY_Tc&t=18s) (32:41)

## Background Information

### Accepting GitHub Assignments

With each assignment in CSC232, students are given a URL that must be followed. When the student follows the given URL, a process is kicked off wherein a new repository is created in their GitHub account. Once the repository is created by this background process, the student may clone the repository and work with it as required.

### Cloning a GitHub Repository

Cloning a repository is rather simple. When viewing a GitHub repository online, there is a green button that provides you with the URL needed to clone the repository, as shown here:

![Image of repo clone button](clone-button.png)

When you tap on that button, you actually have two different options for cloning, either via SSH or via HTTPS. While using SSH is more secure, it takes some additional configuration on your part that is beyond the scope of this assignment. As such, you'll want to select HTTPS.

Once you have obtained the repository's URL, cloning is done by simply executing the following `git` command:

```bash
git clone https://github.com/msu-csc232/hw00-your-github-username.git
```

Please note the following:

1. The above command assumes the name of the repository is `hw00-your-github-username`. When your instructor creates assignments, they'll always have a prefix like `hw00` (for homework 0) followed by a hyphen followed by your GitHub username. As such, you shouldn't type that command verbatim. Instead, substitute the URL following the word `clone` with whatever you copied by tapping on the clone button on your repository when viewewd online in GitHub.
1. Before issuing this `git` command, it is assumed you have navigated to the folder in which you want this repository cloned. For example, before doing this, you may want to create a "working" directory for this class with the following commands:

```bash
$ mkdir -p csc232/hw
$ cd csc232/hw
$ git clone https://github.com/msu-csc232/hw00-your-github-username.git
Cloning into 'hw00-your-github-username.git'...
remote: Counting objects: 5, done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
$ cd hw00-your-github-username
```

Again, in the above commands, one does not type the `$`. Any lines shown without the leading `$` are output from one of the commands. Also, when executing the `git` command, you may be prompted to (minimally) log in to GitHub as shown here:

![GitHub Login Window](github-login.png)

Also, if you've set up two-factor authentication (something you should do with any online accounts that offer it, including social media like Facebook) you may be prompted for secondary authentication as shown here:

![Multifactor Authentication](two-factor-auth.png)

When you're all said and done, you'll be in the csc232/hw/hw00-your-github-username directory. This cloned directory is what will be referred to as your "working directory."

### Creating a develop branch

With each assignment, you will be required to create a `develop` branch within which to do your work. Creating the `develop` branch will allow you to create a _pull request_ which will be the manner in which you submit your assignments.

Creating a `develop` branch is easy. Assuming you're in your "working directory" for the assignment and you've just cloned this repository for the first time, issuing the following `git` commands will yield something like:

```bash
$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean

$ git checkout -b develop
Switched to a new branch 'develop'

$ git branch
* develop
  master

$
```

In the above, we see three new `git` commands:

1. `git status` will tell you what branch your on and whether or not there are changes to be committed.
1. `git checkout -b` is actually two commands in one: the `checkout` portion is how you switch to a different branch; the `-b` switch is used to create the branch first. If you already have the branch, we do this command with out the `-b` to switch to the desired branch.
1. `git branch` shows the branches that currently exist in your local repository. The one with the leading `*` is the branch that is currently checked out.

### Modifying Existing Files and Commiting Changes

Now that we have a `develop` branch to work in, let's modify an existing [file](version.txt). In this repository is a file named `version.txt`. The contents of this file can be seen with the `cat` command in the Git Bash console window:

```bash
$ cat version.txt
Version: 0.0

$
```

Open this file using Notepad and change version number to be 1.0. You can easily open Notepad using the following command:

```bash
$ notepad version.txt
$
```

Make the change, save the file and close Notepad. (If you are using a non-Windows machine, just open this file with your favorite text editor.)

Now that this file has changed, we want to _commit_ this change. This is easily done as follows:

```bash
$ git commit -am "Updated version number."
[master 7333fbb] Updated version number.
 1 file changed, 1 insertion(+), 1 deletion(-)
$
```

Note:

* the "commit hash" (`7333fbb`) is unique to this example; it'll most likely be different on your machine.
* The `-am` switches on the `git commit` command serve two purposes: the `a` part serves to "stage" this file for commits and the `m` portion serves to indicate a commit message that must accompany every commit. If you leave off the `m` portion, you'll find yourself in a weird editor (named `vi`) whose usage is beyond the scope of this assignment.

### Adding New Files Under Revision Control and Commiting Changes

Sometimes you'll find the need to _add_ new files to a repository. In order for these new files to be recognized under the `git` version control system, we have to _stage_ the file. This too, is pretty simple. Let's use Notepad to create a new file named `bio.md`:

```bash
$ notepad bio.md
$
```

The above command will launch Notepad. You may be prompted to "bind" `bio.md`; just select "Yes" in the dialogue box presented by Notepad. (And again, if you're using a non-Windows machine, just use your favorite text editor to create this file.)

The `md` extention on this file suggests it is in the Markdown format. You don't have to style the file using Markdown (you can just write plain text for now), but you are encourage to learn the Markdown syntax as this is the "standard" format for README files (and other documentation hosted in version control systems like GitHub, BitBucket and the like). Here's a [cheat sheet](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf) specific to GitHub that may be used to help with the Markdown syntax.

What should be written? Your instructor would like to know more about you; what's your background, what's your major, why did you pick your major etc. Your instructor also likes to be humored, so tell him something funny. None of this has to be real; it's up to you as to what you want to say here. You could also tell him things you like (music, football, etc.). It is rumored that he gives bonus points for anything positive said about the Buffalo Bills. This can be as long (or as short) as you desire; it could be as close or as far as possible from reality. The content is not important; it's the skill of adding a new file to your repository.

When you're all done, _save_ your changes, _add_ and _commit_ them under revision control:

```bash
$ git add bio.md
$ git commit -m "Initial import of bio."
... some output regarding changes and modes created
$
```

### Pushing Your Work to GitHub

At this point, we have made several changes to the contents of our repository under the `develop` branch. We have:

* _edited/modified_ a file and commited those changes
* _created_ a new file, _added_ it revision control and committed the changes in this new file

Now it's time to _push_ these changes back to GitHub. We'll do this using the `git push` command. However, since we've created this `develop` branch locally on our computer, GitHub knows nothing about this branch. As such, with this _first_ push to GitHub, we have to tell GitHub to create a similarly named branch and set up _tracking_ between GitHub's `develop` branch and our local `develop` branch. We do this by using the `--set-upstream origin develop` switch with the `git push` command as follows:

```bash
$ git push --set-upstream origin develop
Counting objects: 6, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 2.26 KiB | 578.00 KiB/s, done.
Total 6 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 2 local objects.
To github.com:msu-csc232/hw00-your-github-username.git
 * [new branch]      develop -> develop
Branch 'develop' set up to track remote branch 'develop' from 'origin'.

$
```

Any subsequent push does not require the `--set-upstream` switch (and in fact, it shouldn't be used once it's been used once already). That is, all subsequent pushes merely require that you type `git push` at the command line.

### Creating a Pull Request

When we're done, the `develop` branch will be different from the `master` branch. These differences amount to the work you've done. A _pull request_ is issued to ask others to review these changes before they're _merged_ into the `master` branch. In other words, your "requesting" to "pull" the changes you've made into the `master` branch; hence the name _pull request_.

Before a pull request can be created, we have two more things to do. We have to

1. _commit_ the changes we've made in this `develop` branch.
1. _push_ our changes to GitHub.

As we've just done this, we can issue our pull request. Back on GitHub, our repository has a "Pull Request" tab as shown below:

![GitHub Pull Request](pull-request.png)

Tap on the New Pull Request button and make sure you are comparing your `develop` branch with your `master` branch as shown below:

![Compare Branches](compare-branches.png)

Note the direction of the arrow: _from_ `develop` _into_ `master`. Tap on the Pull Request button and fill in a brief description. Also, add professordaehn as a reviewer and assign yourself the Assignee. Once you've added in all these details, tap on the Create Pull Request button.

Once you've done this, _do not merge_ until your instructor as approved the pull request.

## Tasks

To complete this assignment, one must:

1. Accept the assignment delivered to you (i.e., visit the URL given)
1. Clone their `hw00-*` repository.
1. Create a `develop` branch within in which to do your work.
1. Modify a [file](version.txt) with a simple change and commit your changes.
1. Create a new file in which you'll write a brief bio and outline your expectations for the class.
1. Add the new file to version control and commit your changes.
1. Push your changes to GitHub.
1. Create a pull request requesting to merge your changes in your `develop` branch into your `master` branch. (This pull request must have "professordaehn" added as a reviewer.)

## Issues

If you have found any issues with this lab, e.g., the output of a command didn't match yours, or you have found typos, or one or more sections are worded in a manner that seems confusing or misleading, please bring it to my attention. The best way to do that is to "raise an Issue." Visit [https://github.com/msu-csc232-fa19/hw00/issues](https://github.com/msu-csc232-fa19/hw00/issues) and tap on the "New Issue" button.
