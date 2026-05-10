# Install Git

Installing being normal user or root.

```bash
# Normal user
sudo apt install git
```

```bash
# Root user
apt install git
```
# Usage

To start using Git, go inside the directory or folder and perform the command below.

```bash
git init
```
# Git ignore

Sometimes we don't need to track specific files and folders, that's where `.gitignore` appears. This files ignore tracking files to the version history, allows us to avoid conflicts in some files.

## Ignore files and directories

1. Create the `.gitignore` file.

```bash
vim .gitignore
```

2. Ignore just typing the name.

```bash
Aircrack-ng.md
```

>[!info] Remember
>The `Aircrack-ng.md` file, won't be tracked.

3. Save the `.gitignore` file and commit the changes.

## Ignore files and directories including exceptions

We can ignore a bunch of files but making some exceptions. You can perform this actions with a few lines.

1. Open the `.gitignore` file.

```bash
vim .gitignore
```

2. Ignore all files except specific ones.

```bash
# Ignore all the files
*

# Except
!Catpuccin.md
```

3. Save and commit the changes.

# More about ignoring files

https://stackoverflow.com/questions/987142/make-gitignore-ignore-everything-except-a-few-files

https://www.delftstack.com/howto/git/git-ignore-everything-except

# Git links for cheat sheet

https://www.freecodecamp.org/news/git-cheat-sheet/

https://www.geeksforgeeks.org/how-to-fix-git-remote-repository-not-found-error/
