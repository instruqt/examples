---
slug: inspect-git-files
id: on9gck6gehfr
type: challenge
title: Inspect Git files
teaser: Learn a bit about how git works under the hood.
notes:
- type: text
  contents: |-
    Executing git init creates a .git subdirectory in the current working directory, which contains all of the necessary Git metadata for the new repository.
    This metadata includes subdirectories for objects, refs, and template files.
    A HEAD file is also created which points to the currently checked out commit.
tabs:
- title: Shell
  type: terminal
  hostname: shell
difficulty: basic
timelimit: 900
---
🔍 Let's examine
===============
## Your repository

Take a look inside the files in the *.git* directory inside your newly created repository.

```
cd my-repo/.git
ls
```