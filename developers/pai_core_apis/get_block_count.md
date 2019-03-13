---
layout: default
title: GetBlockCount
parent: PAI Core Apis
grand_parent: Developer Reference
---

GetBlockCount
========================

The `getblockcount` RPC returns the number of blocks in the local best block chain.

*Parameters: none*

*Result---the number of blocks in the local best block chain*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The number of blocks in the local best block chain.  For a new node with only the hardcoded genesis block, this number will be 0"

{% enditemplate %}

*Example from PAI Core 0.10.0*

```
pai-cli -testnet getblockcount
```

Result:

```
315280
```

*See also*

* `GetBlockHash`: returns the header hash of a block at the given height in the local best block chain.
* `GetBlock`: gets a block with a particular header hash from the local block database either as a JSON object or as a serialized block.