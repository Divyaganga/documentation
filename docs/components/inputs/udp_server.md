---
title: udp_server
type: input
status: deprecated
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/input/udp_server.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

:::warning DEPRECATED
This component is deprecated and will be removed in the next major version release. Please consider moving onto [alternative components](#alternatives).
:::

```yaml
# Config fields, showing default values
input:
  udp_server:
    address: 127.0.0.1:0
    delimiter: ""
    max_buffer: 1000000
```

Creates a server that receives messages over UDP as a continuous stream of data.
Each line is interpretted as an individual message, if the delimiter field is
left empty then line feed (\n) is used.

The field `max_buffer` specifies the maximum amount of memory to
allocate for buffering lines of data, this must exceed the largest expected
message size.

