# Git

The version control software everybody loves.

# Contents:

- [Git](#git)
- [Contents:](#contents)
- [Tips:](#tips)
  - [Git commit standards:](#git-commit-standards)
  - [When branching and it refuses to push the branch:](#when-branching-and-it-refuses-to-push-the-branch)
  - [Adding remote to a not cloned, local repo:](#adding-remote-to-a-not-cloned-local-repo)
  - [Correcting last commit message or commit content:](#correcting-last-commit-message-or-commit-content)
  - [Retrieving files from previous commits:](#retrieving-files-from-previous-commits)

# Tips:

## Git commit standards:

Example: `fix(email back-end): corrected sender email`

As described on: 
https://www.conventionalcommits.org/en/v1.0.0-beta.2/#summary.

## When branching and it refuses to push the branch:

`git push -u origin --all`

As described on: 
https://stackoverflow.com/questions/23401652/fatal-the-current-branch-master-has-no-upstream-branch.

## Adding remote to a not cloned, local repo:

`git remote add origin (link)`

To check the added remote, or to delete it:

`git remote`

`git remote rm (remote name)`

## Correcting last commit message or commit content:

You should avoid correcting other commit messages.

`git commit --amend -m "New commit message."`

The contents of the modified staging area also change the commit.

## Retrieving files from previous commits:

`git checkout (commitHash) -- (fileName)`