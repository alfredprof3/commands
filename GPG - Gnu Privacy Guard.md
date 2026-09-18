# GPG - How to use

Installation
-----

Install the most recent version of GNU Privacy Guard.
`sudo apt install gnupg2`


Generating the Key
-----

Generate your private key (private keys never expire)
`gpg2 --expert --full-generate-key`

Follow the interactive prompts:

    * Select (9) ECC and ECC for key types.
    * Choose (1) Curve25519 for encryption and Ed25519 for signing (it may be the default).
    * Enter a key expiration (e.g., 2y for 2 years, or 0 for no expiration).
    * Provide your user ID: real name, email, and optional comment.
    * Enter a strong passphrase to secure your private key.


Verifying your keys
-----

List public keys.
`gpg2 --list-keys --keyid-format=LONG`

List secret keys.
`gpg2 --list-secret-keys --keyid-format=LONG`


Expiration date
-----

List your keys
`gpg2 --list-keys`

Look for the line below `pub  ed25519 2020-09-11 [SC] [expires: 2020-09-21]`

For example: We want to edit key AF4RGH94ADC84
`gpg2 --edit-key AF4RGH94ADC84`

```bash
gpg> list

sec     ed25519/AF4RGH94ADC84
        created: 2020-09-11     expires: 2020-09-21     usage: SC
        trust: ultimate         validity: ultimate
ssb     cv25519/56ABDJFDKFN
        created: 2020-09-11     expires: 2020-09-21     usage: E
[ultimate] (1). John Doe <johndoe@mail.com>
```

We want to edit the first subkey (ssb). When you select key (1), you should see the `*` next to it such as `ssb*`

```bash
gpg> key 1
gpg> expire     # set the expiration date
gpg> save
```

Now select the main private key

```bash
gpg> key 0
gpg> expire     # set the expiration date
gpg> save
```


Backup your private keys
-----

Backup and export your private key.
`gpg2 --export-secret-keys --armor > private_key.asc`


References
-----

1. https://docs.gitcode.com/en/docs/help/gpg/
2. https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key
3. https://blog.justme.ovh/posts/gpg-complete-guide-encryption-signing/
4. https://gist.github.com/jfrobbins/5c2dbceb81c33afc5b0bcbe0d3343692
