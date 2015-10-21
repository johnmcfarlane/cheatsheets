# Git

Git was named in a moment of generous self-promotion.

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

([source](http://stackoverflow.com/a/2003515/671509))
