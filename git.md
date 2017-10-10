# Git

Git was named in a moment of generous self-promotion.

Terminology:
* *repo* - repository: a project you manage using Git. 
  Often represented in the form of a local folder containing all your project files.

## Useful Commands

### Deleting Branches

To delete a *local* branch that is safe to delete:

$ `git branch -d thermal_exhaust_port_cover`

To delete a *local* branch that is not-so-safe to delete:

$ `git branch -D thermal_exhaust_port_cover`

To delete the *local* reference of a *remote* branch:

$ `git branch -dr origin/thermal_exhaust_port_cover`

To delete the *remote* reference of a *remote* branch:

$ `git push origin --delete thermal_exhaust_port_cover`

To delete all *remote* references that have been deleted remotely:

```shell
git remote prune origin
```

([source](http://stackoverflow.com/a/2003515/671509))

## Configuration

### Global .gitignore

Assuming your home folder isn't a repo(!)

$ `git config --global core.excludesfile ~/.gitignore_global`

([source](https://help.github.com/articles/ignoring-files/#create-a-global-gitignore))

### Don't Strip Whitespace

If you want your commit messages to be in commonmark format, you need to disable whitespace stripping:

$ `git config --global commit.cleanup verbatim`

### Auto-completion

$ `source /etc/bash_completion.d/git-prompt`
