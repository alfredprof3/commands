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

# Vim Plugins
- [auto pairs](https://github.com/jiangmiao/auto-pairs)
- [vim-closetag](https://github.com/alvan/vim-closetag)
- [vim Completes Me](https://github.com/vim-scripts/VimCompletesMe)
- [css complete](https://github.com/othree/csscomplete.vim)
- [emmet](https://github.com/mattn/emmet-vim)
- [nerdcommenter](https://github.com/preservim/nerdcommenter)
- [nerdtree](https://github.com/preservim/nerdtree)
- [vim airline](https://github.com/vim-airline/vim-airline)
- [vim devicons](https://github.com/ryanoasis/vim-devicons)
- [vim surround](https://github.com/tpope/vim-surround) or [vim sandwich](https://github.com/machakann/vim-sandwich)
- [vim visual multi](https://github.com/mg979/vim-visual-multi)
- [vim snippets](https://github.com/honza/vim-snippets) or [UltiSnips](https://github.com/sirver/ultisnips)
- [html5](https://github.com/othree/html5.vim)

# Vim Colorschemes
- [Papilio Dehaanii](https://github.com/keiyakeiya/PapilioDehaanii.vim)
- [Nightfly](https://github.com/bluz71/vim-nightfly-colors)
- [Omni](https://github.com/yonlu/omni.vim)

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
# Download plugins script

```bash
#!/bin/bash

echo "Type the Github URL"
read github

echo "Type the folder name"
read dirName

git clone --depth=1 $github ~/.vim/pack/plug-ins/start/$dirName/
```
