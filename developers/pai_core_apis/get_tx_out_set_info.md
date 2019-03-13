---
layout: default
title: GetTxOutSetInfo
parent: PAI Core Apis
grand_parent: Developer Reference
---

GetTxOutSetInfo
========================

The `gettxoutsetinfo` RPC returns statistics about the confirmed unspent transaction output (UTXO) set. Note that this call may take some time and that it only counts outputs from confirmed transactions—it does not count outputs from the memory pool.

*Parameters: none*

*Result---statistics about the UTXO set*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "object"
  p: "Required<br>(exactly 1)"
  d: "Information about the UTXO set"

- n: "→<br>`height`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The height of the local best block chain.  A new node with only the hardcoded genesis block will have a height of 0"

- n: "→<br>`bestblock`"
  t: "string (hex)"
  p: "Required<br>(exactly 1)"
  d: "The hash of the header of the highest block on the local best block chain, encoded as hex in RPC byte order"

- n: "→<br>`transactions`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The number of transactions with unspent outputs"

- n: "→<br>`txouts`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The number of unspent transaction outputs"

- n: "→<br>`bytes_serialized`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The size of the serialized UTXO set in bytes; not counting overhead, this is the size of the `chainstate` directory in the pai Core configuration directory"

- n: "→<br>`hash_serialized`"
  t: "string (hex)"
  p: "Required<br>(exactly 1)"
  d: "A SHA256(SHA256()) hash of the serialized UTXO set; useful for comparing two nodes to see if they have the same set (they should, if they always used the same serialization format and currently have the same best block).  The hash is encoded as hex in RPC byte order"

- n: "→<br>`total_amount`"
  t: "number (pai's)"
  p: "Required<br>(exactly 1)"
  d: "The total number of pai's in the UTXO set"

{% enditemplate %}

*Example from Pai Core 0.10.0*

```
pai-cli -testnet gettxoutsetinfo
```

Result:

```
{
    "height" : 315293,
    "bestblock" : "00000000c92356f7030b1deeab54b3b02885711320b4c48523be9daa3e0ace5d",
    "transactions" : 771920,
    "txouts" : 2734587,
    "bytes_serialized" : 102629817,
    "hash_serialized" : "4753470fda0145760109e79b8c218a1331e84bb4269d116857b8a4597f109905",
    "total_amount" : 13131746.33839451
}
```

*See also*

* `GetBlockChainInfo`: provides information about the current state of the block chain.
* `GetMemPoolInfo`: returns information about the node’s current transaction memory pool.