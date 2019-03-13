---
layout: default
title: GetInfo
parent: PAI Core Apis
grand_parent: Developer Reference
---

GetInfo
========================

The `getinfo` RPC prints various information about the node and the network.

{{WARNING}} `getinfo` was removed in 0.16.0 version of Pai Core. Use the RPCs listed in the See Also subsection below instead.

*Parameters: none*

*Result---information about the node and network*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "object"
  p: "Required<br>(exactly 1)"
  d: "Information about this node and the network"

- n: "→<br>`version`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "This node's version of Pai Core in its internal integer format.  For example, Pai Core 0.9.2 has the integer version number 90200"

- n: "→<br>`protocolversion`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The protocol version number used by this node.  See the [protocol versions section][section protocol versions] for more information"

- n: "→<br>`walletversion`"
  t: "number (int)"
  p: "Optional<br>(0 or 1)"
  d: "The version number of the wallet.  Only returned if wallet support is enabled"

- n: "→<br>`balance`"
  t: "number (pai's)"
  p: "Optional<br>(0 or 1)"
  d: "The balance of the wallet in pai's.  Only returned if wallet support is enabled"

- n: "→<br>`blocks`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The number of blocks in the local best block chain.  A new node with only the hardcoded genesis block will return `0`"

- n: "→<br>`timeoffset`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The offset of the node's clock from the computer's clock (both in UTC) in seconds.  The offset may be up to 4200 seconds (70 minutes)"

- n: "→<br>`connections`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "The total number of open connections (both outgoing and incoming) between this node and other nodes"

- n: "→<br>`proxy`"
  t: "string"
  p: "Required<br>(exactly 1)"
  d: "The hostname/IP address and port number of the proxy, if set, or an empty string if unset"

- n: "→<br>`difficulty`"
  t: "number (real)"
  p: "Required<br>(exactly 1)"
  d: "The difficulty of the highest-height block in the local best block chain"

- n: "→<br>`testnet`"
  t: "bool"
  p: "Required<br>(exactly 1)"
  d: "Set to `true` if this node is on testnet; set to `false` if this node is on mainnet or a regtest"

- n: "→<br>`keypoololdest`"
  t: "number (int)"
  p: "Optional<br>(0 or 1)"
  d: "The date as Unix epoch time when the oldest key in the wallet key pool was created; useful for only scanning blocks created since this date for transactions.  Only returned if wallet support is enabled"

- n: "→<br>`keypoolsize`"
  t: "number (int)"
  p: "Optional<br>(0 or 1)"
  d: "The number of keys in the wallet keypool.  Only returned if wallet support is enabled"

- n: "→<br>`paytxfee`"
  t: "number (pai's)"
  p: "Optional<br>(0 or 1)"
  d: "The minimum fee to pay per kilobyte of transaction; may be `0`.  Only returned if wallet support is enabled"

- n: "→<br>`relayfee`"
  t: "number (pai's)"
  p: "Required<br>(exactly 1)"
  d: "The minimum fee a low-priority transaction must pay in order for this node to accept it into its memory pool"

- n: "→<br>`unlocked_until`"
  t: "number (int)"
  p: "Optional<br>(0 or 1)"
  d: "The Unix epoch time when the wallet will automatically re-lock.  Only displayed if wallet encryption is enabled.  Set to `0` if wallet is currently locked"

- n: "→<br>`errors`"
  t: "string"
  p: "Required<br>(exactly 1)"
  d: "A plain-text description of any errors this node has encountered or detected.  If there are no errors, an empty string will be returned.  This is not related to the JSON-RPC `error` field"

{% enditemplate %}

*Example from PAI Core 0.10.0 with wallet support enabled*

{% highlight bash %}
pai-cli -testnet getinfo
{% endhighlight %}

Result:

```
{
    "version" : 100000,
    "protocolversion" : 70002,
    "walletversion" : 60000,
    "balance" : 1.27007770,
    "blocks" : 315281,
    "timeoffset" : 0,
    "connections" : 9,
    "proxy" : "",
    "difficulty" : 1.00000000,
    "testnet" : true,
    "keypoololdest" : 1418924649,
    "keypoolsize" : 101,
    "paytxfee" : 0.00000000,
    "relayfee" : 0.00001000,
    "errors" : ""
}
```

*See also*

* `GetBlockChainInfo`:
* `GetMemPoolInfo`:
* `GetMiningInfo`:
* `GetNetworkInfo`:
* `GetWalletInfo`: