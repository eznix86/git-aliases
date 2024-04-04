# git-aliases

Use `git config -e --global` to open `vi` to edit config.

Paste these:

```sh
[alias]
    cleanup = "!git branch --merged | grep -Ev '(^\\*|master|main|dev)' | xargs git branch -d && echo 'Merged Branches cleaned ✨'"
    remote-cleanup = "!git branch -r --merged | grep -Ev '(^\\*|master|main|dev)' | xargs -n 1 git push --delete origin && echo 'Merged Remote Branches cleaned ✨'"
```

You will get

```sh
git cleanup # deletes stale branches which has already been merged locally
git remote-cleanup # deletes stales branches which has already been merge remotely
```

Another way is doing

```sh
git config --global alias.undo  "\!git reset --soft HEAD~1" 
git config --global alias.redo  "\!git reset --hard HEAD@{1}"
```

On top of the previous commands you will get

```
git undo # undo last commit without being distructive
git redo # replay the last command
```

Example of `undo` and `redo`
- Lets say you committed something, you messed up. just do `git undo`, now you are let's say you've changed you mind, you want to go back to the original changes. Do `git redo`.
- If you do `git redo`, without a git undo, it will be destructive! Modify it to check in history if you run a git command before. Maybe
