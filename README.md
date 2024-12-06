# git-learn
Let us learn how to use git command


Let us improve efficiency.

Let us cooperate!

## Reset

use the following command to go back to an old commit.
`get reset --hard <commit>`

## Branch

Create branch with `git branch new` 
and go to the branch via `git checkout -b new`

## Merge

merge new to main by `git merge new`

## Action

create `.github/workflows/*.yml`

Example:


```yaml
name: Pytest

on: [push, pull_request]

jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ["3.9", "3.10", "3.11", "3.12"]

    steps:
      - uses: actions/checkout@v3
      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v4
        with:
          python-version: ${{ matrix.python-version }}

      - uses: actions/cache@v3
        id: cache
        with:
          path: ~/.cache/pip
          key: ${{ runner.os }}-pip-${{ hashFiles('**/requirements.txt') }}
          restore-keys: |
            ${{ runner.os }}-pip-

      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt
          pip install pytest

      - name: Run tests
        run: pytest
```


