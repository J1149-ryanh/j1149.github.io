---
layout: default
title: GetRawChangeAddress
parent: PAI Core Apis
grand_parent: Developer Reference
---

GetRawChangeAddress
========================

*Requires wallet support.*

The `getrawchangeaddress` RPC returns a new Pai address for receiving change. This is for use with raw transactions, not normal use.

*Parameters: none*

*Result---a P2PKH address which can be used in raw transactions*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "string (base58)"
  p: "Required<br>(exactly 1)"
  d: "A P2PKH address which has not previously been returned by this RPC.  The address will be removed from the keypool but not marked as a receiving address, so RPCs such as the `dumpwallet` RPC will show it as a change address.  The address may already have been part of the keypool, so other RPCs such as the `dumpwallet` RPC may have disclosed it previously.  If the wallet is unlocked, its keypool will also be filled to its max (by default, 100 unused keys).  If the wallet is locked and its keypool is empty, this RPC will fail"

{% enditemplate %}

*Example from Pai Core 0.10.0*

```
pai-cli -testnet getrawchangeaddress
```

Result:

```
mnycUc8FRjJodfKhaj9QBZs2PwxxYoWqaK
```

*See also*

* GetNewAddress:
* GetAccountAddress: