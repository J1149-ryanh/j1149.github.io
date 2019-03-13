---
layout: default
title: WalletPasshraseChange
parent: PAI Core Apis
grand_parent: Developer Reference
---

WalletPasshraseChange
=======================

*Requires wallet support.  Requires an encrypted wallet.*

The `walletpassphrasechange` RPC changes the wallet passphrase from ‘old passphrase’ to ‘new passphrase’.

`WARNING: if using this RPC on the command line, remember
that your shell probably saves your command lines (including the
value of the passphrase parameter).`

*Parameter #1---the current passphrase*

{% itemplate ntpd1 %}
- n: "Current Passphrase"
  t: "string"
  p: "Required<br>(exactly 1)"
  d: "The current wallet passphrase"

{% enditemplate %}

*Parameter #2---the new passphrase*

{% itemplate ntpd1 %}
- n: "New Passphrase"
  t: "string"
  p: "Required<br>(exactly 1)"
  d: "The new passphrase for the wallet"

{% enditemplate %}

*Result---`null` on success*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "null"
  p: "Required<br>(exactly 1)"
  d: "Always set to JSON `null`"

{% enditemplate %}

*Example from Pai Core 0.10.0*

Change the wallet passphrase from "test" to "example":

```
pai-cli -testnet walletpassphrasechange test example
```

(Success: no result printed.)

*See also*

* `EncryptWallet`: encrypts the wallet with a passphrase. This is only to enable encryption for the first time. After encryption is enabled, you will need to enter the passphrase to use private keys.
* `WalletPassphrase`: stores the wallet decryption key in memory for the indicated number of seconds. Issuing the walletpassphrase command while the wallet is already unlocked will set a new unlock time that overrides the old one.
* `WalletLock`: removes the wallet encryption key from memory, locking the wallet. After calling this method, you will need to call walletpassphrase again before being able to call any methods which require the wallet to be unlocked.