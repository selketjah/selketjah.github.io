---
layout: post
title: My git flow for contributing to an open source repository
category: OSS
date: February 06, 2018
tags:
- OSS
- F#
---

You can contribute to an open source repository by submitting Pull Requests to the project maintainers.
In order to do that, you need to set up the project first.

<!--more-->

# Initial setup

## Fork the repository

A fork is a copy of a repository and allows you to contribute safely to project.
You can create a fork by clicking the matching button in the repository.

![Fork button]({{ site.baseurl }}public/images/fork.PNG)

## Clone your fork

If you go back to your profile, you will see that a copy of repository was added to your personal repositories. Clone your copy of the repository locally.

`git clone https://github.com/your_username/yourrepo.git`

To see the current configuration of your remote repository type the following command:

`git remote -v`

Add the repo to your current configuration

`git remote add upstream https://github.com/oss_username/theirrepo.git`

If you list the current configuration again, you will see that the upstream repository has been added to your configuration.

![git configuration origin and upstream]({{ site.baseurl }}public/images/configuration.png)
_origin_ is your forked remote repository.
_upstream_ is the original remote repository

# Contributing

## Create a branch and push it to your fork

Checkout master and create a branch.

`git checkout -b yourbranchname`

Make your changes, commit it locally and push it to your fork.

`git add ...`

`git commit -m 'descirption of commit here'`

`git push --set-upstream origin yourbranchname`

## Create a pull request

Now you can create a pull request to have your changes merged. Go to your fork and click the button 'new pull request'.
You will see a screen similar to the one below.

![create pull request]({{ site.baseurl }}public/images/openpullrequest.png)

Fill in the title and add a small description and press 'create pull request'.
And that's it, you just made your first contribution to Forge!

# Sync fork

Before you make a second contribution, you may need to sync your fork.

`git fetch upstream`

If you are not on your local master branch, checkout master

`git checkout master`

Merge the changes made to the upstream branch into your local branch and push it to your fork's remote branch.

`git merge upstream/master`

`git push origin master`