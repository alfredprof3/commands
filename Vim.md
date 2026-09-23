# Neovim Installation

METHOD 1. Install From Source (Recommended)
-----

1. Install build prerequisites on your system.

`sudo apt-get install ninja-build gettext cmake curl build-essential git linux-headers-$(uname -r)`

2. Clone the repository in `/opt` path.

```bash
cd /opt
git clone htttps://github.com/neovim/neovim.git
```

3. Select the stable release.

```bash
cd neovim
git checkout stable
```

4. Compile neovim.

```bash
sudo make CMAKE_BUILD_TYPE=Release      # or CMAKE_BUILD_TYPE=RelWithDebInfo for debugging info
sudo make install
```

5. Create the `.deb` package

```bash
cd build
sudo cpack -G DEB
```

6. Install the `.deb` package.

`sudo dpkg -i nvim-linux-(arch).deb      # with (arch) either x86_64 or arm64`

7. Run `nvim --version` to verify the version and the installation.


Updating Neovim Installed from Source
-----

1. Navigate to your local Neovim source directory in your terminal.

```bash
cd /opt/neovim
git fetch
git log -l              # confirm the latest commit date matches recent updates
git checkout stable
git pull
```

2. Clean any previous build artifacts if necessary and compile the updated source code.

```bash
sudo make CMAKE_BUILD_TYPE=RelWithDebInfo
cd build
sudo cpack -G DEB
```

3. Install the new `.deb` package created.

`sudo dpkg -i nvim-linux-(arch).deb      # with (arch) either x86_64 or arm64`

4. Run `nvim --version` to verify that the version number has successfully updated.


METHOD 2. Install from a Tarball
-----

1. Download the tarball from the official GitHub repository.

```bash
cd /opt
curl -L -O https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz
```

2. Extract the tarball.

`sudo tar -zxvf nvim-linux-x86_64.tar.gz`

3. Remove the downloaded `tar.gz` file.

`sudo rm -v nvim-linux-x86_64.tar.gz`

4. Add Neovim to your System `PATH` in your current shell (`.bahsrc` or `.zshrc`).

`export PATH="$PATH:/opt/nvim-linux-x86_64/bin"`

5. Reload your shell configuration to apply the changes

`source ~/.bashrc       # or source .zshrc`

6. Verify the installation.

`nvim --version`

sudo rm -rf /opt/nvim-linux-x86_64
sudo tar -C /opt -xzf nvim-linux-x86_64.tar.gz
rm nvim-linux-x86_64.tar.gz


Usage
-----

`nvim`

Creating a new file with Vim

```bash
vim newFile.txt
```

Open an existing file

```bash
vim file.txt
```

Open a file in Normal Mode:

```vim
:open Scripts/text.sh
```

# Keyboard

Split screen vertical:
`<C-w>v`

Split screen at bottom
`<C-w>s`

Move to the left window:
`<C-w>l`

Move to the right window:
`<C-w>h`

Move up window:
`<C-w>k`

Move down window:
`<C-w>j`

Increase windows size
`<C-w> >`

Reduce windows size
`<C-w> <`

Increase height
`<C-w> +`

Reduce height
`<C-w> -`

Reset the width and height of windows:
`<C-w> =`

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
- [vim-airline-clock](https://github.com/enricobacis/vim-airline-clock.git)

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

Reference
-----

1. [Vim learning - Learn Vim in your browser](https://ridhsuki.github.io/vim-learning/#modes-intro)
