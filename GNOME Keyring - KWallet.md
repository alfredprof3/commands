# GNOME Keyring - KWallet

To store safely secrets, passwords, tokens or other private stuff, libsecret with the Secret Service API can handle this. The `libsecret` is a library for storing and retrieving passwords and other secrets. It communicates with the Secret Service API using D-Bus. gnome-keyring and ksecretservice are both implementations of a Secret Service.


Installation
-----

Install `gnome-keyring` or `kwallet`
```bash
sudo apt install gnome-keyring
sudo apt install kwallet6 kwalletcli
```

To inspect what is stored, use a GUI tools: Passwords and Keys (seahorse) for GNOME Keyring, and KWallet Manager for KWallet.
```bash
sudo apt install seahorse
sudo apt install kwalletmanager
```

Also we need `libsecret` to keep passwords and secrets safe using key-strong encryption.
`sudo apt install libsecret-1-0 libsecret-1-dev libsecret-tools`


Usage examples
-----

To use Git and `libsecret` together, first we need to compile it.
```bash
cd /usr/share/doc/git/contrib/credential/libsecret/
sudo make
git config --global credential.helper /usr/share/doc/git/contrib/credential/libsecret/git-credential-libsecret
```


Managing secrets from the command line
-----

The secret-tool utility (part of libsecret) lets you store and retrieve secrets in scripts without needing a GUI.
`secret-tool store --label="github_pat_1234567890" service GitHub username alfredxuser`

To see your private key.
secret-tool lookup service GitHub username alfredxuser

To delete your private key.
secret-tool clear service GitHub username alfredxuser
