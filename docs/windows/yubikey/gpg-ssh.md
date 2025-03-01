---
title: SSH with GPG via Yubikey
description: Guide on how to use a Yubikey on Windows to authenticate SSH sessions with GPG keys
---

# SSH with GPG via Yubikey

## Objective

Establish authentication with GPG between a Windows client and a Linux server via yubikey. 

## Requirements

 - Yubikey with OpenPGP capability
 - [Gpg4win](https://www.gpg4win.org/download.html) - GPG agent for Windows
 - [kleopatra](https://apps.kde.org/kleopatra/) - Graphical interface for key management
 - [optional] [Pageant](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) if you want to use PuTTY - PuTTY's agent
 - SSH server with configued firewall

## Sources

 - Yubico - [SSH Authentication to GitHub Using a YubiKey on Windows](https://developers.yubico.com/PGP/SSH_authentication/Windows.html)
 - Yubico - [Using Your YubiKey with OpenPGP](https://support.yubico.com/hc/en-us/articles/360013790259-Using-Your-YubiKey-with-OpenPGP)
 - My dad's notes

## Guide

### Key management on Windows

```bat title="Generate a key"
:: Arguments: name, algorythm, use, expiration
gpg --quick-generate-key name@address.com ed25519 auth never
``` 

!!! warning "Do **NOT** choose to save the changes"
    It will destroy the key on your computer, and it can't be retrieved from the Yubikey.

```bat title="Copy the key to the Yubikey"
gpg --edit-key name@address.com
keytocard

:: Enter Q to exit
:: Do NOT save when prompted to, it will destroy the key on your computer !
```

We need to export the public key in SSH format in order to store it on the server. The easiest way is to use Kleopatra. <br>
Open Kleopatra. The generated key should appear on the main tab. If it isn't there, click on `Certificates` at the top and `Refresh certificates`.  Double click on the certificate and, in the newly opened window, click on the `Subkeys` tab. There, you can right-click on the key to export it as an OpenSSH key. 

Lastly, the GPG agent needs to be restarted to take the key into account. You can put the following in the `C:\Users\<user>\AppData\Roaming\Microsoft\Windows\Start Menu\` folder so it would be executed on login. 

```bat title="GPG_Starter.bat" linenums="1"
:: Stop existing GPG instances
gpg-connect-agent "KILLAGENT" /bye
:: Launch new instance
gpg-connect-agent /bye
``` 

Here is another version that launches PuTTY:

```bat title="launcher.bat" linenums="1"
:: Stop existing GPG instances
gpg-connect-agent "KILLAGENT" /bye
:: Launch new instance
gpg-connect-agent /bye
:: Launch PuTTY. "start" allows the script to close immediatly.
start putty.exe
```

!!! info "PuTTY configuration"
    If you're using PuTTY, make sure that `Attempt authentication using Pageant` is checked in Connection > SSH > Auth 

### Key management on Linux

In your session, paste the previously exported key on a new line in `.ssh/authorized_keys`.

### Debug 

If needed, logs can be viewed rapidly with the following command:

```bash
journalctl -u ssh -S "year-mm-dd hh:mm:ss"
```

!!! info "Verbosity"
    Log verbosity can be enhanced by tweaking the following line:

    ```bash title="/etc/ssh/sshd_config" linenums="26"
    # Logging
    #SyslogFacility AUTH
    LogLevel DEBUG3
    ```



