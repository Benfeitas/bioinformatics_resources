# Cheatsheet for renv

- `renv::init()`   # initialize project
- `renv::snapshot()`   # update env
- `renv::restore()`  # restore project state
- `renv::activate()` # activate project script


To restore a previous project:
1. renv::settins$external.libraries(.libPaths())
2. renv::activate()
3. renv::restore()
