# Clang format Github action

This project can be used to run clang-format on every push using Github actions. Uses ~~Microsoft~~ **.clang-format file** codestyle by default.

**Clang-Format runs in the branch that triggers the action (in the code below, it's always the master branch)**
**It also doesn't format files in the components/ directory.**

## Usage

For a more detailed installation guide look [there](https://github.com/MarvinJWendt/run-node-formatter/wiki)

Create a `formatter.yml` file in `.github/workflows/`.
Paste this code into the file:

```yml
name: "Run Clang-Format in Cpp files"

# Controls when the action will run. 
on:
  # Triggers the workflow on push or pull request events but only for the master branch
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  lint:
    name: clang-format Code Formatter
    runs-on: ubuntu-latest
    steps:
    - name: Clang Code Formatter
      uses: luccareinehr/clang-format-action@master
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
