# git-commands Cheatsheet
Useful set of git commands to remeber

Initial repository clone, repository URL can be of type HTTP or SSH if using RSH key. Often SSH clone is used with git interface to VSTS repo

```
# URL Examples
HTTP_URL="https://github.com/MyCompany/project-dev.git"
SSH_URL="git@github.com:MyCompany/project-dev.git"

git clone <repo name URL HTTP/SSH>
```

Create New Feature Branch
Make new branch from `master` branch

```javascript
git checkout -b name-my-feature-branch
```

Sometime forgetful `.gitignore` `.DS_Store` once commited annoying to clean up.
How to remove it from remote `.DS-Store` tracking run set of these commands from project root directory removes from all subdir on the masteer branch.

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
this process will save 2 files in user home directory
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

There are times we need to start with empty directory. Regular gitflow will allways have master branch with full code and otehr branches will be feature extensions. this case when we need to add feature that should not ahve impact to existing code such as Salesforce metadata is good example, to add new fields to custom object we do not want to redeploy entire massive ORG master. for this case can create `empty` branch taht has no files in it andd keep it empty.
we clone `empty` to start, then we create our feature branch from empty and add new code to it then commit only feaature branch. 

```
git clone <REPO NAME>
cd <REPO NAME DIRECTORY>
# We are in master branch now
git checkout empty
# we are in empty branch and directory is empty
git checkout -b <new branch name>
git branch

# Make some changes, add files to setup new branch like /src directoy and package.xml

# create Source directory
mkdir src
# copy base setup for deployemnt
cp ../../basedev/sample-package.xml src/package.xml

# setup remote branch as remote in repo by push new branch
git push origin <FEATURE BRANCH NAME>
```

To commit changes to this new feature/story branch always use origin.

```
git push origin <FEATURE BRANCH NAME>
```