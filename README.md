# git-commands Cheatsheet
Useful set of git commands to remeber

Sometime forgetful `.gitignore` `.DS_Store` once commited anoying to clean up.
How to remove it from remote .DS-Store tracking run set of these commands from project root directory.

```javascript
find . -name ".DS_Store" -exec git rm --cached -f {} \;.
git commit -m "delete files"
git push
```

