# GCM Configuration - Headless environment

To configure Git Credential Manager (GCM) with GnuPG / pass on a completely stripped-down, headless Debian 13 Trixie environment (with no GUI, no desktop utilities, and only raw TTY access), you must build out the underlying system architecture step-by-step.

Because you are using an ultra-minimal kernel-level installation, utilities that are usually pre-installed are entirely missing. This manual guide details how to install and wire up each layer of the dependency stack from scratch.


Understanding the Architecture: How it Links Together
-----

Before typing commands, it helps to understand what happens when you run git clone:

   1. Git needs to authenticate. It looks at credential.helper and invokes the binary git-credential-manager.
   2. GCM reads your configurations and sees it must use the gpg store backend.
   3. GCM calls the Linux utility pass to securely fetch or save the token.
   4. pass talks to gpg, which requires your master passphrase.
   5. gpg invokes gpg-agent, which triggers pinentry-tty to draw a secure, interactive passphrase prompt directly inside your active TTY screen.


Step 1: Install Missing Core Dependencies
-----

Since your system lacks common system utilities, you must install the absolute minimum toolkit required to download, extract, and run GCM alongside the security toolchain.

Install text-based utilities, encryption engines, and curl for downloading binaries
-----

`sudo apt install -y git gnupg pass pinentry-tty curl tar`


Step 2: Manually Install Git Credential Manager (GCM)
-----
Because Debian repositories do not always pack the latest .deb packages for GCM natively, downloading the official self-contained Linux tarball ensures it has all its independent runtime dependencies.

1. Download the official Linux GCM tarball:

`curl -LO https://github.com`

2. Create a safe directory for GCM and extract it:

```bash
sudo mkdir -p /usr/local/share/gcm-core
sudo tar -xvf gcm-linux_amd64.2.6.1.tar.gz -C /usr/local/share/gcm-core
```

3. Create a Symlink: This creates a system-wide execution path so Git can instantly recognize the program when looking for manager.

`sudo ln -sf /usr/local/share/gcm/git-credential-manager /usr/local/bin/git-credential-manager`

4. Run GCM's native configuration routing:

`git-credential-manager configure`

5. Verify Git can now see it:

`git credential-manager --version`


Step 3: Establish the Encryption Pair (gpg & pass)
-----

Now we establish the encrypted database system. You must generate a cryptographic key pair to sign and password-protect your credential store files.

1. Generate your GPG master key:

`gpg --expert --full-generate-key`

Follow the onscreen prompts. Provide your name, email, and a secure master passphrase.

2. Retrieve your GPG Key ID:

`gpg --list-secret-keys --keyid-format=LONG`

Look for the line starting with sec. Copy the alphanumeric string right after the slash (e.g., sec rsa3072/1A2B3C4D5E6F7G8H). That string is your Key ID.

3. Initialize pass:

`pass init <YOUR_KEY_ID_HERE>`

This creates an encrypted directory at ~/.password-store/ dedicated to holding strings managed by GCM.


Step 4: Configure Git's Storage Protocol
-----

Tell Git exactly what storage mechanism GCM should default to when processing usernames and personal access tokens (PATs).

**Clear any conflicting or duplicate credential entries**

`git config --global --unset-all credential.helper`

**Direct Git to delegate authentication to the GCM binary link**

`git config --global credential.helper manager`

**Instruct GCM to hand off plaintext strings to 'pass' for encryption**

`git config --global credential.credentialStore gpg`


Step 5: Wire up the headless TTY Prompting Engine
-----

In a pure TTY, if a program requests a password without a graphical window, it will instantly hang or crash unless it knows which screen virtual node to print to.

1. Update your shell profile: Open ~/.bashrc (or ~/.profile) with a terminal text editor like nano:

`vim ~/.bashrc`

Add these three lines to the very bottom of the file:

```bash
export GPG_TTY=$(tty)
export DISPLAY=
export DBUS_SESSION_BUS_ADDRESS=
```

Why this matters: GPG_TTY=$(tty) dynamically assigns your exact current terminal line number to GnuPG. Clearing DISPLAY and DBUS hard-prevents GnuPG from attempting to lookup graphical popups that do not exist. Save and exit (Ctrl+O, Enter, Ctrl+X).

2. Configure gpg-agent: Edit or create your agent profile:

`vim ~/.gnupg/gpg-agent.conf`

Ensure it has the exact following entries:

`pinentry-program /usr/bin/pinentry-tty`

(Note: As you mentioned, keep pinentry-mode loopback deleted or out of this file entirely, as pinentry-tty interacts interactively, which behaves differently from a loopback stream).

3. Configure gpg.conf: Open your general GPG configuration:

`vim ~/.gnupg/gpg.conf`

Ensure the following line is added:

`pinentry-mode default`

4. Reload Environment: Drop and restart the background GPG daemon to absorb your absolute configuration parameters:

```bash
source ~/.bashrc
gpg-connect-agent reloadagent /bye
```


Step 6: Testing the Integration End-to-End
-----

Validate the system piece-by-piece to ensure no errors interrupt your workflow.

1. Perform a manual pipeline check:

`pass insert git/test-validation`

If successful, a secure gray text frame will overlay your TTY asking for your master GPG passphrase. Type it in.

2. Verify read success:

`pass show git/test-validation`

3. Trigger Git: Execute your git clone <private-repository-url> command.

* GCM will launch inside your terminal loop.
* Type your GitHub Username.
* Paste your GitHub Personal Access Token (PAT) when prompted for the password.
* It will ask for your master GPG passphrase one final time to lock it away.

Any consecutive Git requests on that repository or matching domain will silently look up the encrypted tree structure via pass, completely bypassing authentication prompts from this point forward.
