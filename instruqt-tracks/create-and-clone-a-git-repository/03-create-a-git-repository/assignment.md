---
slug: create-a-git-repository
id: waanr1xhplui
type: challenge
title: Create a Git repository
teaser: Creating repositories with Git
notes:
- type: text
  contents: |-
    The git **init** command creates a **new Git repository**.
    It can be used to **convert an existing**, unversioned project to a Git repository or **initialize a new**, empty repository.

    Most other Git commands are **not available outside** of an initialized repository, so this is usually the first command you'll run in a new project.
tabs:
- title: Shell
  type: terminal
  hostname: shell
difficulty: basic
timelimit: 900
---
✏️ Let's create a repository
===========================
## Getting started

To start working with Git, you need a repository.
Start by creating your first repository in the folder **my-repo**

```
git init -q my-repo
```