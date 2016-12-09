# git-commands Cheatsheet
Useful set of git commands to remeber

Create New Feature Branch
Make new branch from `master` branch

```javascript
git checkout -b name-my-feature-branch
```

Sometime forgetful `.gitignore` `.DS_Store` once commited anoying to clean up.
How to remove it from remote .DS-Store tracking run set of these commands from project root directory.

```javascript
find . -name ".DS_Store" -exec git rm --cached -f {} \;.
git commit -m "delete files"
git push
```

