# How To's about Debian


How To Copy/Paste From Clipboard in a Headless Debian Environment
-----

**METHOD 1. General Purpose Mouse**

Install `gpm` (General Purpose Mouse).

`sudo apt install gpm`

Enable it on start up.

`sudo systemctl enable --now gpm`

Once installed, you can click and drag to highlight text and paste it using the middle mouse button.

**METHOD 2. Using Terminal Multiplexer (tmux)**

Install tmux.

`sudo apt install tmux`

Start a tmux session.

`tmux`

Enter in **copy mode** by pressing.

`Ctrl b` + `Shift {`

Press `Ctrl Space` to start highlighting text.

Press `Ctrl w` to copy the text into the tmux buffer and exit copy mode.

Paste it by pressing `Ctrl b` + `Shift }`
