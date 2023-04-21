# Centralized Pre-commit hooks
Centralized Pre-commit hook is a centrally managed hook that helps you manage and enforce pre-commit checks for your project's code. 

## Pre-requisites
You need to install the `pre-commit` python package in your system.
```bash
pip install pre-commit
```
## How to setup
1. Make sure your repository is a git repository
2. You first need to define a pre-commit configuration file called `.pre-commit-config.yaml` in the root of your project.
Here's an example .pre-commit-config.yaml file:
```yaml
repos:
 -  repo: https://github.com/farazkhan7/raz-centralized-precommit-hook
    rev: v1.0.0
    hooks:
    -   id: centralized-hook

```
3. Once you have the config file in place, install the pre-commit hooks in your repo. You can do so by:
```bash
pre-commit install
```

## How to run
The pre-commit hooks run only on files that you have already staged;
meaning that you have already performed the `git add` command on them
So if you have not staged your changes yet, you can do so with the following
command
```
git add .
```

Now, the pre-commit script will check your project's formatting when you attempt
to commit your code with `git commit`. Commit is approved only when the pre-commit script finds your
code well formatted and documented.

Note: You can also run the pre-commit script without attempting to commit (for test purposes).
Use the command below to run the pre-commit script manually.
```
pre-commit run --all-files
```

Important Note: Sometimes when you commit your code, black or isort could make changes to your files
making them unstaged, specially when the commit failed on pre-commit checks. In such case, you
need to stage those files back with `git add` and then commit again with `git commit` 

## Bypassing pre-commit hooks
While it is generally not recommended to bypass pre-commit hooks, there are situations where you may need to do so. To bypass pre-commit hooks and commit code without running any checks, you can use the `--no-verify` option with the `git commit` command.

Here's an example of how to bypass pre-commit hooks and commit code without running any checks:
```bash
git commit --no-verify -m "Commit message"
```