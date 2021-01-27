---
title: inproc
type: output
status: stable
categories: ["Utility"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/output/inproc.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


```yaml
# Config fields, showing default values
output:
  inproc: ""
```

Sends data directly to Benthos inputs by connecting to a unique ID. This allows
you to hook up isolated streams whilst running Benthos in
[streams mode](/docs/guides/streams_mode/about), it is NOT recommended
that you connect the inputs of a stream with an output of the same stream, as
feedback loops can lead to deadlocks in your message flow.

It is possible to connect multiple inputs to the same inproc ID, resulting in
messages dispatching in a round-robin fashion to connected inputs. However, only
one output can assume an inproc ID, and will replace existing outputs if a
collision occurs.

