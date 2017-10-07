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

Set up SSH key with Github for secure clone repo etc.
In MAC user root directory generate rsh key and save it in github with these commands.
this porcess will save 2 files in user home directory
.ssh/id_rsa. and .ssh/id_rsa.pub.

```javascript
$ ssh-keygen -t rsa

Generating public/private rsa key pair.
Enter file in which to save the key (home/.ssh/id_rsa)
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /Users/home/.ssh/id_rsa.
Your public key has been saved in /Users/home/.ssh/id_rsa.pub.
The key fingerprint is: <secure key will dispay here>

$ cat .ssh/id_rsa.pub

<SSH-RSA Key will print here, copy this keye and save to Github keys>

```