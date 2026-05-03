# Vim installation

Install

```bash
sudo apt install vim-gtk3
```

Usage

```bash
vim
```

Creating a new file with Vim

```bash
vim newFile.txt
```

Open an existing file

```bash
vim file.txt
```

Open a file in Normal Mode:

`:open Scripts/text.sh`

# Keyboard

Split screen vertical:
\<C-w>v

Split screen at bottom
\<C-w>s

Move to the left, right, up and down window:
\<C-w>l
\<C-w>h
\<C-w>k
\<C-w>j

Increase o reduce windows size in Vim
Increase/reduce the width:
\<C-w> >
\<C-w> <

Increase/reduce the height:
\<C-w> +
\<C-w> -

Reset the width and height of windows:
\<C-w> =

Plugins

- nerdtree
- nightfly-theme
- omni-theme
- vim-airline
- vim-devicons
- visual-multi

# Update Vim plugins

METHOD 1. With one single command

```bash
find ~/.vim/pack/plug-ins/start/ -maxdepth 1 -mindepth 1 -type d -exec git -C {} pull \;
```

METHOD 2. A for loop bash script

```bash
for dir in ~/.vim/pack/plug-ins/start/*/; do
  echo "Updating $(basename $dir)..."
  git -C "$dir" pull
done
```
