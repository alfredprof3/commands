# Shell/Bash scripting

1. Create the sh file

touch first.sh

2. Inside the file, add the shebang `#!` and type the command

#!/bin/bash
echo "My first script in bash"

3. Execute the script

bash first.sh

# Executing a Linux command

1. Declare a variable and print it with the `echo` command to ensure you do it great

#!/bin/bash
var=`pwd` # or another Linux command
echo "Your current working directory is -> $var"

> [!NOTE]
> Is important to type the command inside ˋ ˋ

# Example. Update vim plugins

```bash
#!/bin/bash

for dir in ~/.vim/pack/plug-ins/start/*/; do
  echo "Updating $(basename $dir)..."
  git -C "$dir" pull
done
```

# Music Downloader using Yt-dlp

```bash
#!/bin/bash

echo -e "Yt-dlp music downloader. \nType YouTube ID tag"
read id

echo -e "\nFile format:"; echo "1) MP3"; echo "2) WAV"
read input

case $input in
    1)
        mp3() {
            yt-dlp --extract-audio --audio-format mp3 --audio-quality 320K https://www.youtube.com/watch?v=$id
        }
        mp3
        ;;
    2)
        wav() {
            yt-dlp --extract-audio --audio-format wav https://www.youtube.com/watch?v=$id
        }
        wav
        ;;
esac
```
