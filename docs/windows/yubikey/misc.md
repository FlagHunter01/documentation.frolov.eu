---
title: Miscellaneous
description: Miscellaneous tips about the Yubikey
---

# Miscellaneous

## Reset PGP application

 - Download the deprecated [Yubikey Manager](https://www.yubico.com/support/download/yubikey-manager/)
 - Run the following commands

```bat
cd "C:\Program Files\Yubico\YubiKey Manager"
.\ykman openpgp reset
```

## Set PGP passwords

```bat title="PIN"
gpg  --change-pin
```

```bat title="Personal administration code"
gpg --card-edit
admin
passwd
```

## Card customization

You can use the `gpg-card` facility to customize your Yubikey.

- `name` allows you to asign your real name to a field in the card
-   `salutation` is used to define your genrer ? ([documentation](https://www.gnupg.org/documentation/manuals/gnupg24/gpg-card.1.html))
    !!! quote 
        SALUTATION [--clear] SALUT Change the salutation info for the card. This info can be used by applications for a personalized greeting. The option --clear removes this data object. GnuPG does not use this info.
