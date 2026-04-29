# Git
# 1. Installation
## Linux
Debian/Ubuntu distributions
###### Normal User
```bash
sudo apt install git
```
###### Root User
```bash
apt install git
```
## MacOS
### Homebrew
```sh
brew install git
```
### MacPorts
```sh
sudo port install git
```
#### How to install MacPorts
To see how to install MacPorts refer to the official [MacPorts](https://www.macports.org/install.php) website or through this [[MacPorts|documentation]]
## Windows
[Click here to download](https://github.com/git-for-windows/git/releases/download/v2.51.1.windows.1/Git-2.51.1-64-bit.exe) the latest version of Git for Windows
### Standalone Installer
[Git for Windows /x64 Setup](https://github.com/git-for-windows/git/releases/download/v2.51.1.windows.1/Git-2.51.1-64-bit.exe)
[Git for Windows /ARM64 Setup](https://github.com/git-for-windows/git/releases/download/v2.51.1.windows.1/Git-2.51.1-arm64.exe)
# 2. Setup
General configuration first time
## 1. Setup local or global user name and email
### Global
```sh
git config --global user.name "username"
git config --global user.email "user@email.com"
```
### Local
> [!warning] IMPORTANT
> For `--local` method, you need to be inside the directory.

```sh
git config --local user.name "username"
git config --local user.email "user@email.com"
```
## 2. Verify the configuration
```sh
git config --list
```
## 3. Credential Helper, Credential Store or Git Credential Manager
- [ ] Two screenshot in Xiaomi smartphone to configure Git Credential Manager using Termux #remember
### Linux environment
#### 3.1. GPG and Pass
##### 1. Install GnuPG
```sh
sudo apt install gnupg
```
##### 2. Create the secret key
```sh
gpg --full-generate-key
```
##### 3. List the key
```sh
gpg --list-secret-keys --keyid-format=LONG
```
##### 4. Install Pass; standard password unix manager
```sh
sudo apt install pass
```
##### 5. Create the password vault with Pass
```sh
pass init 0EAB09812894FD90
```
#### 3.2. Git Credential Manager
##### 1. Download and Install Git Credential Manager
```sh
sudo apt install git-credential-manager
```
##### 2. Configure Git
```sh
git-credential-manager configure
```
##### 3. Setup the Credential Store with gpg
```sh
export GCM_CREDENTIAL_STORE=gpg
```
or
```sh
git config --global credential.credentialStore gpg
```
##### 4. Export the GPG_TTY to the profile
Add this line to the `.bashrc` or `.profile` file
```sh
export GPG_TTY=$(tty)
```
### macOS environment
#### MacOS Keychain Git Credential Helper
```sh
git config --global credential.helper osxkeychain
```
#### Alternative with Credential Store using macOS Keychain
```sh
export GCM_CREDENTIAL_STORE=keychain
```
or
```sh
git config --global credential.credentialStore keychain
```
#### Alternative directly with Git Credential Manager
##### 1. Install Git Credential Manager in macOS
```sh
brew install --cask git-credential-manager
```

After macOS git-credential-manager installation, stay up to date with
```sh
brew upgrade --cask git-credential-manager
```
##### 2. Setup Credential Store with Credential Manager
```sh
git config --global credential.credentialStore manager
```
### Windows environment
##### Setup Git Credential Wincred
```sh
git config --global credential.helper wincred
```
### Other alternatives
#### Git Credential Store
##### Global
```sh
git config --global credential.helper store
```
##### Local
```sh
git config --local credential.helper store
```
#### Git Credential Cache
Stores credentials in memory for a short, configurable duration (e.g., 15 minutes). Credentials are not written to disk and are purged when the cache expires.
##### Global
```sh
git config --global credential.helper cache
```
##### Local
```sh
git config --local credential.helper cache
```
#### Linux libsecret
##### Git Credential Libsecret
```sh
git config --global credential.helper libsecret
```

Alternative configure the GCM (Git Credential Manager)
```sh
git config --global credential.helper manager
```
#### More information about Git Credential Manager
[Using Git Credential Manager for Effortless Authentication](https://www.git-tower.com/learn/git/faq/git-credential-manager)
# Usage
To start using Git, we have two options, cloning a repository or initializing. As an example of how to use Git, I'm going to provide a real **Scenarios** where you can learn more about.
## Option 1
### 1. Cloning the repository
Clone the repository inside a directory

```shell
git clone https://github.com/username/repo-name.git
```
### 2. Remote branch
Get inside the directory and be sure we are working in the same remote branch where we clone the repository.

```shell
git remote show origin
```

or

```shell
git remote -v
```
### 3. Push the changes
When we make changes to the repository we need to manually push them.

```shell
git push
```
## Option 2
### 1. Change the directory
You have created a folder or directory, go inside of it and type the next command, to initialize the repository

```sh
git init
```
### 2. Add the changes to stage
Once you have initialize the repository, we need to track the files and move to the stagging area with the following command

```sh
git add example.txt
```
or
```sh
git add .
```
## Scenario 1. Initialize, branching and commit
### Initialize the repo
```bash
git init
```
### Create a new branch
```bash
git branch obsidian
```
### Push the branch to Github
```bash
git push --set-upstream origin obsidian
```
#### More about creating and pushing branches in Github
[Github Branching and Merging: A Step-By-Step Guide](https://axolo.co/blog/p/github-branching-and-merging-step-by-step-guide)
## Delete local and remote branches
###### Deleting local branch
The flag `-d` stands for `--delete`

```bash
git branch -d obsidian
```

###### Deleting the remote branch
To competely delete the branch from the remote repository, perfom the next command

```bash
git push origin --delete obsidian
```

To verify de deletion

```bash
git branch -r
```

After the deletion, clean up local references

```bash
git fetch --prune
```
#### More about deleting branches
[How to Remove a Remote Branch in Git](https://www.geeksforgeeks.org/how-to-remove-a-remote-branch-in-git/)
[How do I delete a Git branch locally and remotely?](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-locally-and-remotely)
[Git Delete Remote Branch – How to Remove a Remote Branch in Git](https://www.freecodecamp.org/news/git-delete-remote-branch/)
[How Delete a Git Branch Locally and Remotely? - GeeksforGeeks](https://www.geeksforgeeks.org/delete-a-git-branch-locally-and-remotely/)
# Git ignore
Sometimes we don't need to track specific files and folders, that's where `.gitignore` appears. This files ignore tracking files to the version history, allows us to avoid conflicts in some files.
###### Create the file
```bash
vim .gitignore
```
###### Ignore just typing the name
A example below.

```bash
Aircrack-ng.md
```

>[!info] Remember
>The `Aircrack-ng.md` file, won't be tracked.
###### Save the file
Save the `.gitignore` file and commit the changes.
## Ignore files and directories including exceptions
We can ignore a bunch of files but making some exceptions. You can perform this actions with a few lines.
###### Open the `.gitignore` file
```bash
vim .gitignore
```
###### Ignore all files except specific ones
```vim
*

!Catpuccin.md
```

> [!info] Syntax
> The asterik inside the file means; ignore all the files, except `!Catpuccin.md`
###### Ignore directories
```vim
*

!.obsidian/
```
###### Save the changes
```vim
:x
```
###### Commit the changes
```sh
git commit -m ".gitignore file updated"
```
#### More about ignoring files
[How to Ignore Everything Except Some Files in Git](https://www.delftstack.com/howto/git/git-ignore-everything-except/)
[Make .gitignore ignore everything except a few files](https://stackoverflow.com/questions/987142/make-gitignore-ignore-everything-except-a-few-files)
[Tips-and-Tricks - Git Documentation - Obsidian Publish](https://publish.obsidian.md/git-doc/Tips-and-Tricks#Gitignore)
# Undo, Go Back or Revert commits in Git
# Git cheat sheet
[Git Cheat Sheet – 50 Git Commands You Should Know](https://www.freecodecamp.org/news/git-cheat-sheet/)
[How to Fix Git ‘remote: Repository not found’ Error? - GeeksforGeeks](https://www.geeksforgeeks.org/how-to-fix-git-remote-repository-not-found-error/)
