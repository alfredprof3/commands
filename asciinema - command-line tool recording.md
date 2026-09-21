# asciinema - How To


Install
-----

The binary last release can be downloaded and placed in these two paths: `/usr/local/bin` or `$HOME/.cargo/bin`

⚠ If you don't have Rust installed, instead place it in the `/usr/local/bin` directory.

```bash
cd /usr/local/bin/ && curl -L -O https://github.com/asciinema/asciinema/releases/download/v3.2.1/asciinema-x86_64-unknown-linux-gnu -o asciinema
sudo chmod 755 asciinema
```

If you have Rust installed and all the variables set, install the binary in the `$HOME/.cargo/bin`

```bash
cd $HOME/.cargo/bin/ && curl -L -O https://github.com/asciinema/asciinema/releases/download/v3.2.1/asciinema-x86_64-unknown-linux-gnu -o asciinema
chmod 755 asciinema
```


Usage
-----

Record a session

`asciinema rec demo.cast`

To stream a session via built-in HTTP server run

`asciinema stream -l`

To stream a session via a relay (asciinema server) run

`asciinema stream -r`


References
-----

1. https://asciinema.org/
