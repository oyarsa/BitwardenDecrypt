# BitwardenDecrypt
Decrypts an encrypted [Bitwarden](https://github.com/bitwarden) data.json file (from the
Desktop App). You can safely store data.json as an encrypted, offline backup of your
vault knowing you will always be able to decrypt it.

To determine the location of the data.json file see:
https://bitwarden.com/help/data-storage/#on-your-local-machine

**Note**: BitwardenDecrypt does not work with Bitwarden Encrypted JSON Exports.
These exports lack the Protected Symmetric Key needed to decrypt entries.

Password Protected Encrypted JSON Exports are supported.

Outputs JSON containing:
- Logins
- Folders
- Organizations
- Collections
- Cards
- Secure Notes
- Identities
- Sends *(Optional)*

**Note**-d: Outputs (almost) all key/value pairs, including ones you probably don't care
about.

### Installation:
```console
$ pip install https://github.com/oyarsa/BitwardenDecrypt
# or (recommended)
$ pipx install https://github.com/oyarsa/BitwardenDecrypt
```

### Usage:
```console
$ bitwarden-decrypt --help
usage: bitwarden-decrypt [-h] [--includesends] [--output OUTPUTFILE]
                         [inputfile]

Decrypts an encrypted Bitwarden data.json file.

positional arguments:
  inputfile            INPUTFILE (default: data.json)

options:
  -h, --help           show this help message and exit
  --includesends       Include Sends in the output. (default: False)
  --output OUTPUTFILE  Saves decrypted output to OUTPUTFILE (default: None)
```

The program will prompt you for the password interactively. This can be either the
master password or the password used to encrypt the JSON file.

## Donate
Find this useful?  If so, consider showing your appreciation. :slightly_smiling_face:
https://paypal.me/GurpreetKang

## Limitations

- Attachments are not supported (they are not stored locally in data.json)
- Does not work with Bitwarden Encrypted JSON Exports.
<br/>*These exports lack the Protected Symmetric Key needed to decrypt entries.*
<br/>(Password Protected Encrypted JSON Exports are now supported)
- ~~No validation of the CipherString.
I.e. No verification of the MAC before decrypting.~~ Now verifies the MAC.
- Can only decrypt EncryptionType: 2 (AesCbc256_HmacSha256_B64).  At the time of writing this is the default used for all entries in the personal vault.
- ~~Does not decrypt anything from a Collection (Organization).~~<br/>Initial support for decrypting items from a Collection (Organization). This adds support for decrypting EncryptionType: 4 (Rsa2048_OaepSha1_B64)

## To Do
[ ] Nothing.
Hopefully Bitwarden will implement an [encrypted export](https://community.bitwarden.com/t/encrypted-export/235) and this script can become obsolete.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* [Kyle Spearrin](https://github.com/kspearrin) for creating [Bitwarden](https://github.com/bitwarden).
* Joshua Stein ([Rubywarden](https://github.com/jcs/rubywarden)) for the reverse engineered Bitwarden documentation.

#
This project is not associated with [Bitwarden](https://github.com/bitwarden) or [Bitwarden, Inc.](https://bitwarden.com/)
