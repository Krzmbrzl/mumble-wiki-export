= Submitting a patch to Mumble =

So you have something you wish to contribute to the Mumble project? Great! There are a few small hoops you'll have to jump through though :)

## Checklist 

* Are you the sole, original author of the work you are submitting? If not, is the original author(s) copyright statement and licensing included?
* Can the work be licensed under the BSD license? This is a requirement for being part of Mumble.
* Is the work based on the current development version of Mumble, and not just the last stable release?

## Necessary information 

We use git, which credits patches both to the author and the commiter. We'll deal with the commiter part, but what we need from you is:

* Your real name (no aliases, please)
* Your prefered email address
* A one-line commit message describing the change.

## Submitting the patch 

Patches ideally should be submitted as pull requests  [github](https://github.com/mumble-voip/mumble to our repository on). Alternatively you can use the instructions below and submit your patch to our old  [sourceforge](https://sourceforge.net/tracker/?group_id=147372&atid=768007 "Patches" tracker on).

= Producing the patch =

Mumble uses git, so your patch will end up in git sooner or later.

## Sending complete files 

Please ''do not'' do this. If someone else has edited the file between the time you started editing and the time your file should be applied, those changes would be overwritten. So "full file" submissions are only accpeted if they don't overwrite any other changes.

## Unified diff 

If you're on *nix, a regular 'diff u', to be applied with '-p1' is acceptable.

## Git format-patch 

This is the prefered method of patch, as it contains name, email, commit log and everything else we need directly in the patch.

= Git crash course =

Here's a short crash course on how to use git with Mumble.

For more information and documentation on Git you may want to check (one of) the following sources:  [website](http://git-scm.com/ official),  [gitref](http://gitref.org/),  [book](http://progit.org/book/ progit),  [guide](http://marklodato.github.com/visual-git-guide/index-en.html visual),  [help](http://help.github.com/ github).

## Installation 

First of all, you need git. Install the suitable package for your distribution.

If you're on Win32, we recommend  [msysgit](http://code.google.com/p/msysgit/) (install it with putting git (and only git) in the path or the "bash only" option -- start the "Git Bash" once you're done). If you (really) need a GUI, check  [tortoiseGit](http://code.google.com/p/tortoisegit/), or alternatively one of the  [GUIs](http://en.wikipedia.org/wiki/Git_%28software%29#Portability other).

## Initial setup 

 git config --global user.name "Your Name"
 git config --global user.email "username@domain.tld"
 git config --global branch.autosetuprebase always

(if, and only if, you are on Windows)
 git config --global core.autocrlf true

## Cloning Mumble 

Make a new directory and go into it:
 cd
 mkdir mumble-git
 cd mumble-git

Clone the upstream Mumble repository:
 git clone git://github.com/mumble-voip/mumble.git .

## Editing 

First, you probably want to make a branch
 git branch --track "mybranchname" origin/master
 git checkout "mybranchname"

You now have a local branch. You can switch back to the original by writing
 git checkout master

And back into your branch again with
 git checkout "mybranchname"

You'll likely want to keep your local branch around until the changes have been accepted upstream.

Now, on "mybranchname", start editing.

## Seeing what you've changed 
 git status
Will show a list of changed files. To add a completely new file, use
 git add "filename"

 git diff
Will show you the differences you've added. Note that if you're adding completely new file, they won't show up in "git diff" -- there's nothing to diff it from.

## Committing your changes 

When you are happy with a set of changes:
 git commit -a -m "Description of changes. This goes in the Changelog for the next release."

If you just want to modify your last commit a bit, you can use
 git commit -a --amend -m "Description of changes."

Note that you should never amend a commit that has made it into the official Mumble repository.

## Throwing away your changes 

If you make a change you are unhappy with, you can reset the file to the last commit.
 git checkout "filename"
Or, if you want everything to go back to the way it was:
 git reset --hard

## Updating changes from upstream (optional) 

 git pull --rebase
Will fetch changes that have been done upstream, and try to integrate them with your changes. If you've edited the same files in the same place that has happened upstream, this will fail with a lot of scary looking error messages. If that happens, we recommend you simply do:
 git rebase --abort

And then seek help from someone more experienced with git to help you.

## Making a patch 
When you are ready to send off the patches, make sure you have commited them all, then write:
 git format-patch --find-copies-harder --patience origin

This will produce a series of files, one for each commit you've made. Submit the files to the patch tracker on sourceforge :)


