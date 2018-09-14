# Saving Progress of a Fantasy Grounds Campaign

Using [git](https://en.wikipedia.org/wiki/Git), GitHub (this site) and a little command-line magic, you can save the progress of campaigns (and revert to previous points). In addition, this technique can also be used to remotely save any file/directory within the Fantasy Grounds system. Please note, this is a manual process, and therefore _should not_ cause issues as reported by some other techniques (such as DropBox/Google Drive).

# Pre-Requisites

This tutorial assumes either you are familiar with git and/or you are on a Mac. The reason for the Mac assumption is that git and Windows is a bit larger installation curve and this walk-through does not touch on that.

- a GitHub Account (if you want to remotely store your changes) having proper credential set up for [remote syncronization](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)
- Git installed on your machine
- General understanding of command-line navigation

# Set-up

## Create a GitHub Repository

If you want, set it to private. This will keep people from downloading it. You can always [share it with other GitHub users](https://help.github.com/articles/inviting-collaborators-to-a-personal-repository/).

![Repository Set-up](https://github.com/DigitalMerlin/FantasyGroundsLibrary/blob/master/images/github-repository.png)

### Get your repository remoe url

![Repository URL](https://github.com/DigitalMerlin/FantasyGroundsLibrary/blob/master/images/repository-url.png)

## Create your new campaign in Fantasy Grounds

Start your campaign as you normally would.

## Initialize your Git repository

From the command line, navigate to your Fantasy Grounds `campaigns` directory and then into the campaign you want to save. Note, you can gloablly save all your campigns by staying in the `campaigns` directory.

[Run the following commands](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/)

- `git init`: initializes git tracking in the directory you are in
- `git remote add origin` `remote-repository-URL`: Sets the new remote, where `remote-repository-URL` was found above in GitHub.

### Some security

The file `campaign.xml` does have your game connection details in it (password). It may be smart to not track this file OR just change your game password each time. 

To omit this file from being tracked and stored in the internet:

`echo "campaign.xml" >> .gitignore`

This will create a `.gitignore` file that omits `campaign.xml`

Verfiy it `cat .gitignore`

## Save changes

As your game (or changes) progress, save and push the files remotely.

- `git add -A`: Adds the files in the local repository and stages them for commit
- `git commit -m` `"First commit"`: Commits the tracked changes. You can change the `"First commit"` as play evolves, (ie `"Save after second session dungeon battle"`)
- `git push -u origin master`: Pushes all files to remote repository.

## Reverting

Each time you save your changes, it creates a [commit](https://stackoverflow.com/questions/43970559/what-is-exactly-meaning-of-commit-command-in-git). The benefit of using git is that you can roll-back and/or revert to these historic point in time. Thus rolling your campaign back to a prior session if you want to be nice a give them a do-over, or if something went sideways. This is also nice when creating your own modules, as you can revert to a prior known good save point if you botched something up.

How to do this, is a bit beyond this tutorial, but Google is your friend here.







