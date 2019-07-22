# Git Workflow

## Git

https://git-scm.com/doc


## Forking workflow

- [GitHub forking workflow](https://guides.github.com/activities/forking/)

- Atlassian also provides a good description of this workflow for their bitbucket.org system that is very similar to github.com, and is a good alternative reference.  https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow


## Getting Started


### Setup

> This happens once to set up your computer.

- install and configure git

  https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setu


### Repository Setup

> This happens once for each new project you are working with.

- fork repository (from "upstream")

  from https://github.com/INTERMAGNET/intermagnet.github.io

  <figure>
    <img src="./main-repo.png" alt="Screenshot of intermagnet.github.io repository"/>
    <figcaption>
      Screenshot of intermagnet.github.io repository.

      - Note the `Code`, `Issues`, and `Pull Requests` links
      - Note the `Clone or download` link
    </figcaption>
  </figure>

- clone fork ("origin")

```bash
git clone https://github.com/{USERNAME}/intermagnet.github.io
```

  <figure>
    <img src="./forked-repo.png" alt="Screenshot of fork of intermagnet.github.io repository"/>
    <figcaption>
      Screenshot of fork of intermagnet.github.io repository.

      - Note the `Forked from` link
      - Note the `Clone or download` link
    </figcaption>
  </figure>


- set up upstream

```bash
cd intermagnet.github.io
git remote add upstream https://github.com/INTERMAGNET/intermagnet.github.io
```


### Checking for updates ("rebasing")

> This happens regularly, to make sure you have the latest view of the "upstream".

https://www.atlassian.com/git/tutorials/merging-vs-rebasing

- check for updates (none yet)
- rebase

```bash
## rebase local master branch against upstream
# - switch to master branch
# - pull from upstream with --ff-only
# - push to origin master
rebase() {
  git checkout master && \
  git fetch --all && \
  git pull --ff-only upstream master && \
  git push origin master
}
```


### Working

- branch

Branches are used to avoid conflicts when multiple people are working on the same project.

```bash
git checkout -b {my-new-feature}
```

- make changes

Use your favorite text editor.
[Visual Studio Code](https://code.visualstudio.com/) is one option, and provides some tools for working with git.


- see what has changed


### Save changes

- add files

Stage changed files to be committed.

> `git diff` lists untracked files and shows

```bash
git add {new-or-changed-file.md}
```

> `git add -i` is an interactive version of git add that can be used to commit
> a subset of changed files and directories.


- commit

Persist changes as a new commit.

```bash
git commit -m 'Commit message describing change'
```

> `git commit -am 'Commit message'` includes all modified *existing* files.
> **New files must be `git add`ed before commit.**

### Submitting changes

- pull request

  > [GitHub forking workflow](https://guides.github.com/activities/forking/)


- (rebase)

## Common problems

```bash

## reset local master branch to upstream/master
# - delete existing local master branch
# - create new local master branch tracking upstream/master
reset_master() {
  git fetch --all && \
  git checkout -b temp_master && \
  git branch -D master && \
  git checkout -b master upstream/master && \
  git branch -D temp_master
}
```
