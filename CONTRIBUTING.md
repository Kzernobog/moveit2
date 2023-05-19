# Contributing to MoveIt

Thanks for getting involved! 

A more detailed description and further information on contributing can be
found at [http://moveit.ros.org/documentation/contributing/](http://moveit.ros.org/documentation/contributing/). This 
document serves as a first-time instruction guide to getting involved with
contributing to MoveIt.

## High level approach

1. Find something to fix/improve
2. Get the code
3. Make changes
4. Go through the PR checklist
5. Make a PR

## New contributor guide
**NOTE**: Ignore this section if you already have some experience collaborating with git.

If you are a `git` first timer, go through the following resources to get familiar with collaborating with git
- [Collaborating with git](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests)
<!-- TODO: add a list of helper git resources -->

## Finding something to work upon

Every new contribution needs to address an existing issue. Comment on an 
existing issue and wait for feedback from an active maintainer. If you have a
feature that you would like to see implemented, create an issue or a discussion
and wait for feedback from the broader community. Further information on
how to choose an area to contribute can be found [here](http://moveit.ros.org/documentation/contributing/).

## Get the code
Assuming you have found something to work upon, follow the steps below to prep
your local machine to make changes

### Preliminaries

Fork the repository using your personal account. This can be done by clicking
on the `fork` button on the official MoveIt repo. Then clone your fork onto
your local machine. Follow MoveIt build [instructions](https://moveit.ros.org/install-moveit2/source/)
to setup your local ROS2 MoveIt workspace.

```
cd $COLCON_WS/src
git clone git@github.com:<your-username>/moveit2
```

Ensure you have a remote setup to track the main MoveIt2 repository
```
# If the upstream remote has not been added yet
git remote add upstream https://github.com/ros-planning/moveit2
# upstream has to be the remote of the ros-planning/moveit2
git fetch upstream
# make sure that you are on the master branch
git checkout master
# rebase your master branch on the upstream master
git rebase upstream/master
# push to the master branch of your fork
git push
```

Always ensure that the master branch of your fork mirrors that of upstream.

Make a copy of a branch of your dev environment.

```
git checkout -b <ros-version> upstream/<ros-version> # could be foxy/humble/galactic
```
Create the branch where you will make your changes. You should use this branch
as your test branch, where you develop, profile and test your code.
```
git checkout -b <your-local-branch>
git push -u origin <your-local-branch>
```

It is from this branch that you will create a Pull Request after going through
the Pull Request checklist.

### Working on features

The previous section gets you acquainted with the workflow of getting your own feature 
branch started. Next up, how do you change, develop and contribute to the main repository?

After isolating a particular issue to work on from the issue list, go ahead and create your
local branch as directed in the previous section.

You should ensure that you are on your local feature branch
```
git branch
# should output <your-local-branch>
```

Go ahead and develop and change whatever that needs to be changed. Keep pulling
the changes to the upstream main branch and rebasing them into your local
feature branch. This is good practice as it keeps your local branch up-to-date
with the remote changes. You can do this with the following recipe.

```
# save all existing changes in local branch
git stash 
# Switch to the upstream branch with remote changes
git checkout <tracked-upstream-branch> 
# pull all changes
git pull
# checkout your local branch
git checkout <your-local-branch>
# pull changes into your own local branch
git rebase <tracked-upstream-branch>
# continue your feature development
git stash apply
```






<!--TODO: -->
