# Pass - Standard Unix Password Manager

Installation
-----

Using `apt` in Debian
`sudo apt install pass`


Setting up
-----

First, initialize your vault using your private gpg2 key.
`pass init <PRIVATE_KEY>`


Usage
-----

Save a password in the root folder of the password manager `.password-store`
`pass insert <username>`

List your passwords saved.
`pass list`

Show a specific saved password.
`pass show <username>`

⚠ Type your passphrase generated with your gpg2 private key.

Copy the password to the clipboard.
`pass -c <username>`

Edit the password with the text editor set in the variable `$EDITOR`
`pass edit <username>`

Create a folder and store your password inside.
`pass insert gmail/username`

Select and show a specific password inside a folder.
`pass show gmail/username`


References
-----

1. https://www.passwordstore.org/
