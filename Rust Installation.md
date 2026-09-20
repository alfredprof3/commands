# Rust Installation - How To

Install Rust with rustup
-----

1. Install the prerequesites.

`sudo apt install curl ca-certificates build-essential`

2. Run the official installer.

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

Follow the on-screen options for the interactive menu.

3. Load the environment file in the current shell.

`source ~/.cargo/env`

Verify the toolchain in the current shell.

`rustc --version && cargo --version`


Update Rust
-----

If Rust came from rustup, execute the following command.

`rustup update`


Remove Rustup on Debian
-----

`rustup self uninstall`

Confirm the toolchain directories are gone.

```bash
for path in ~/.cargo ~/.rustup; do
  [ -e "$path" ] && echo "still present: $path" || echo "removed: $path"
done
```


References
-----

1. [How to Install Rust on Debian 13, 12 and 11](https://linuxcapable.com/how-to-install-rust-on-debian-linux/)
2. [Install Rust](https://rust-lang.org/tools/install/)
