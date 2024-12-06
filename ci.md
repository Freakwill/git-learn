# CI

## basic
.travis/
.travis.yml

```yaml
language: python

python:
  - "3.9"     # current default Python on Travis CI
  - "3.10"
  - "3.11"
  - "3.12"
# command to install dependencies
install:
  - pip install -r requirements.txt
  - pip install poetry
  - poetry build

before_script: 
  - pip install pyrimidine
  - pip install pytest

script:
  # :- "./.travis/run.sh"
  - pytest .travis/test.py

deploy:
  provider: releases
  file:
    - dist/*.whl
    - dist/*.tar.gz
  file_glob: true
  on:
    repo: Freakwill/pyrimidine
    tags: true
  skip_cleanup: true

```

## pytest



