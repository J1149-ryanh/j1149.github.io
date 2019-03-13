---
layout: default
title: GetMemoryInfo
parent: PAI Core Apis
grand_parent: Developer Reference
---

GetMemoryInfo
========================

Added in PAI Core 0.14.0*

The `getmemoryinfo` RPC returns information about memory usage.

*Parameters: none*

*Result---information about memory usage*

{% itemplate ntpd1 %}
- n: "`result`"
  t: "object"
  p: "Required<br>(exactly 1)"
  d: "An object containing information about memory usage"

- n: "→<br>`locked`"
  t: "string : object"
  p: "Required<br>(exactly 1)"
  d: "An object containing information about locked memory manager" 
  
- n: "→→<br>`used`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Number of bytes used"

- n: "→→<br>`free`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Number of bytes available in current arenas"

- n: "→→<br>`total`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Total number of bytes managed"

- n: "→→<br>`locked`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Amount of bytes that succeeded locking"

- n: "→→<br>`chunks_used`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Number allocated chunks"

- n: "→→<br>`chunks_free`"
  t: "number (int)"
  p: "Required<br>(exactly 1)"
  d: "Number unused chunks"
  
{% enditemplate %}

*Example from PAI Core 0.14.1*

```
pai-cli getmemoryinfo
```

Result:

```
{
  "locked": {
    "used": 0,
    "free": 65536,
    "total": 65536,
    "locked": 65536,
    "chunks_used": 0,
    "chunks_free": 1
  }
}

```

*See also*

* `GetMemPoolInfo`: