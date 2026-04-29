# Clean installation with desktop environment

sudo apt install gnome-session gnome-shell gnome-backgrounds gnome-applets gnome-control-center mutter gjs gnome-terminal

# List manually installed packages. The command listed below show us the installed packages performed by the user.

comm -23 <(apt-mark showmanual | sort u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)

# DISABLE - METHOD 1. Feedback password

sudo mv /etc/sudoers.d/pwdfeedback /etc/sudoers.d/pwdfeedback.disabled

# DISABLE - METHOD 2. Feedback password

1. Open the editor.

sudo visudo
or
visudo

2. Search the line containing `pwdfeedback` and delete it.

- Option 1

Defaults   env_reset~~,pwfeedback~~

- Option 2

`Defaults   env_reset`
`~~Defaults   pwfeedback~~`

3. Save the file.

# ENABLE. Feedback password

1. Open the editor.

sudo visudo
or
visudo

2. Find the line.

Defaults   env_reset

3. Add the `pwdfeedback`

- Option 1

Defaults   env_reset,pwfeedback

- Option 2

`Defaults   env_reset`
`Defaults   pwfeedback`

# Change default web browser

xdg-settings set default-web-browser microsoft-edge.desktop
