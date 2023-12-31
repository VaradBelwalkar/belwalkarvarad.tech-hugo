---
title: "Assymetric Cryptography using GPG"
date: 2023-01-14T09:15:19+05:30
draft: false
ShowToc: false
ShowRelatedContent: true
summary: "gpg commands for assymetric cryptography"
tags: ["Cryptography", "Linux"]
categories: ["Linux","Cryptography"]
---

### Here are some useful and common commands to use for asymmetric cryptography using gpg.

To create new key :

```shell
gpg --full-generate-key
```

To show public keys with their fingerprints:

```shell
gpg --list-keys
```

To show private keys with their fingerprints(same as their associated public keys' fingerprints)

```shell
gpg --list-secret-keys
```

To export public key:

```shell
gpg --armor --export <fingerprint>
(armor means export in ascii format)
```

To export private key:

```shell
gpg --armor --export-private-keys <fingerprint>
```

To encrypt file with pubkey of one recipient:

```shell
gpg --encrypt --recipient <name or email as per pubkey>  file_to_encrypt
```

To encrypt file with pubkey of multiple recipients (follow another file along with this file to understand the workflow)

```shell
gpg --encrypt --recipient <r1> --recipient <r2> --recipient <r3>  file_to_encrypt
```

To decrypt the file with the private key ( Please note that
there is always associated a metadata with the file which
tells the key id i.e name or email so gnupg takes only that)

(private key which matches the metadata, if it doesn't find it returns error that it cannot decode)

```shell
gpg --decrypt file_to_decrypt
```

To get keygrip:

```shell
gpg --list-keys --with-keygrip
```

To get in machine readable format:

```shell
gpg --list-keys --with-colons
```

To delete a key-pair, you first need to delete the private key:

```shell
gpg --delete-secret-keys <name or email or fingerprint>
```

Then delete the public key:

```shell
gpg --delete-key <name or email or fingerprint>
```

To import a key (doesn't matter whether it is public key or private key)

```shell
gpg --import <key_file>
```

To dearmor a .asc key, i.e key in ascii format do this :

```shell
sudo gpg -o <path_to_outout_key.gpg> .asc_key --dearmor
```

(NOTE: NEVER CREATE KEYS WITH SAME NAME OR EMAIL, THIS CAN MAKE BIG PROBLEMS WHILE USING OR DELETING THE KEYS)
