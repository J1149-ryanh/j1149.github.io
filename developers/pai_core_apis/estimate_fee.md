---
layout: default
title: EstimateFee
parent: PAI Core Apis
grand_parent: Developer Reference
---

EstimateFee
========================

The `estimatefee` RPC estimates the transaction fee per kilobyte that needs to be paid for a transaction to be included within a certain number of blocks.

*Parameter #1---how many blocks the transaction may wait before being included*

{% itemplate ntpd1 %}
- n: "Blocks"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The maximum number of blocks a transaction should have to wait before it is predicted to be included in a block. Has to be between 2 and 25 blocks"

{% enditemplate %}

*Result---the fee the transaction needs to pay per kilobyte*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "number (pais)"
  p: "Required<br>(exactly 1)"
  d: "The estimated fee the transaction should pay in order to be included within the specified number of blocks.  If the node doesn't have enough information to make an estimate, the value `-1` will be returned"

{% enditemplate %}

*Examples from pai Core 0.14.1*

```
pai-cli estimatefee 6
```

Result:

```
0.00162556
```

Requesting data the node can't calculate (out of range):

```
pai-cli estimatefee 100
```

Result:

```
-1
```

*See also*

* SetTxFee: sets the transaction fee per kilobyte paid by transactions created by this wallet.