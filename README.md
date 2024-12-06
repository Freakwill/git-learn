# git-learn

Let us learn how to use git command and GitHub

Let us improve efficiency.

Let us cooperate!

## Reset

use the following command to go back to an old commit.
`get reset --hard <commit>`

Reset the current branch to the state of the commit specified by the n-th previous commit in the commit history, discarding all changes made after that commit and moving the HEAD pointer to that commit.
`get reset --hard Head@{n}`

## Branch

Create branch with `git branch new` 
and go to the branch via `git checkout new`

## Merge

merge new to main by `git merge new`

## Action

create `.github/workflows/*.yml`

Example:
```yaml
name: MyAction

on: [push, pull_request]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Print OK
        if: contains(github.event.head_commit.message, 'print')
        run: echo "OK!"
```

