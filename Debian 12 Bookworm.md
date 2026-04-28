# Clean installation with desktop environment

```bash
sudo apt install gnome-session gnome-shell gnome-backgrounds gnome-applets gnome-control-center mutter gjs gnome-terminal
```

This performs a very lightweight desktop system and environment.

## List manually installed packages
The command listed below show us the installed packages performed by the user.

`comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)`

## Enable / Disable feedback password for terminal
To disable password feedback (asterisks `****`) in Linux, remove or comment out the pwfeedback option in the sudoers file. The most effective methods are removing `/etc/sudoers.d/pwdfeedback` renaming it, or editing `/etc/sudoers` with `visudo` to delete `,pwdfeedback` from the defaults line.

### Disable

#### METHOD 1. Remove/Rename the Sudoers File

```sh
sudo mv /etc/sudoers.d/pwdfeedback /etc/sudoers.d/pwdfeedback.disabled
```

Alternative, if that file does not exist, look for `/etc/sudoers.d/0pwfeedback` and remove it.

#### METHOD 2: Edit sudoers via visudo

1. Open the editor.

- Normal user

sudo visudo

- Root user

visudo

2. Search the line containing `pwdfeedback` and delete it.

- Option 1

Defaults   env_reset,pwfeedback

- Option 2

Defaults   env_reset
Defaults   pwfeedback

3. Save the file. Now you can type, you will see an asterisks while typing your password.

### Enable

1. Open the editor.

- Normal user

sudo visudo

- Root user

visudo

### Additional 

You can create a file called `pwfeedback` and write `Defaults   pwfeedback` inside.

# Change default web browser

xdg-settings set default-web-browser microsoft-edge.desktop
