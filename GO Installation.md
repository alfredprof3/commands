# GO - How To Install


Installation Steps
-----

1. Remove any previous Go installation by deleting the /usr/local/go folder (if it exists), then extract the archive you just downloaded into /usr/local, creating a fresh Go tree in /usr/local/go:

```bash
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.27.1.linux-amd64.tar.gz
```

*(You may need to run each command separately with the necessary permissions, as root or through sudo.)*

Do not untar the archive into an existing `/usr/local/go` tree. This is known to produce broken Go installations.

2. Add `/usr/local/go/bin` to the PATH environment variable.

You can do this by adding the following line to your $HOME/.profile or /etc/profile (for a system-wide installation):

```bash
export PATH=$PATH:/usr/local/go/bin
```

Note: Changes made to a profile file may not apply until the next time you log into your computer. To apply the changes immediately, just run the shell commands directly or execute them from the profile using a command such as source $HOME/.profile.

3. Add `$HOME/go/bin` (the default Go bin path) to your PATH environment variable to use tools installed via go install.

You can do this by adding the following line to your $HOME/.profile or $HOME/.bashrc file:

```bash
export PATH="$PATH:$(go env GOPATH)/bin"
```

4. Downloading the `tar` file.

```bash
cd /usr/local/ && curl -L -O https://go.dev/dl/go1.27.1.linux-amd64.tar.gz
tar -xvf go1.27.1.linux-amd64.tar.gz
```

5. Restart any open terminal sessions for the changes to take effect.

6. Verify that you've installed Go by opening a command prompt and typing the following command:

```bash
go version
```

7. Confirm that the command prints the installed version of Go.
