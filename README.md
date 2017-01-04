# git-commands Cheatsheet
Useful set of git commands to remeber

Create New Feature Branch
Make new branch from `master` branch

```javascript
git checkout -b name-my-feature-branch
```

Sometime forgetful `.gitignore` `.DS_Store` once commited annoying to clean up.
How to remove it from remote `.DS-Store` tracking run set of these commands from project root directory removes from all subdir.

```javascript
find . -name .DS_Store -print0 | xargs -0 git rm --ignore-unmatch
git commit -m "delete files"
git push
```

It is helpful to set up global rule for all git repositories

```javascript
echo ".DS_Store" >> ~/.gitignore_global
echo "._.DS_Store" >> ~/.gitignore_global
echo "**/.DS_Store" >> ~/.gitignore_global
echo "**/._.DS_Store" >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

