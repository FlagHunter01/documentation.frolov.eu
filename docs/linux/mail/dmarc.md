---
title: DMARC
description: How to setup DMARC
---

How to setup DMARC to use with Exim4. 

## Sources

### SPF

!!! note "This section is missing"

### DKIM

- [Exim](https://www.exim.org/exim-html-current/doc/html/spec_html/ch-dkim_spf_srs_and_dmarc.html)
- [transip](https://www.transip.eu/knowledgebase/3199-using-dkim-with-ubuntu-debian)
- [Dev Galaxy](https://dev1galaxy.org/viewtopic.php?id=5340) - Bind bind.keys problem

### DMARC

!!! note "This section is missing"

## Requirements

- Openssl
- Exim4
- Configured Bind9

## Guide

### SPF

!!! note "This section is missing"

### DKIM

Genrate a key and export it in a format suitable for DNS records:

```
openssl genpkey -algorithm ed25519 -out dkim-ed25519.private
openssl pkey -outform DER -pubout -in dkim-ed25519.private | tail -c +13 | base64
```

In the Exim configuration, in the transport section in `remote_smtp` (customize `domain.com`):

```
  dkim_domain = domain.com
  dkim_selector = dkim-ed25519
  dkim_private_key = /etc/exim4/dkim-ed25519.private
```

Add the DKIM field to Bind's configuration (customize `domain.com`). Replace `xxx` with the previously exported key:

```
dkim-ed25519._domainkey.domain.com. IN TXT "v=DKIM1; k=ed25519; t=y; p=xxx"
```

!!! info "`t=y`"
    This is a "testing" tag. Replace it with `t=s` once you have confirmed that DKIM works as intended.

!!! warning "Don't forget to increment the serial"

Restart Exim and Bind.

??? failure "managed-keys-zone: Unable to fetch DNSKEY set '.'"
    Bind stores the Root Trust Anchors in a file named bind.keys. 

    For some reason, after these operations Bind might be unable to find this file. 
    If this error occurs, add the following to its options file:

    ```title="/etc/bind/named.conf.options"
    bindkeys-file "/etc/bind/bind.keys";
    ```

??? info "Time to take effect"
    Remember that these changes need to go through DNS propagation and are not instantaneous.


### DMARK

!!! note "This section is missing"
