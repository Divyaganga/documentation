---
title: hdfs
type: input
status: stable
categories: ["Services"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/input/hdfs.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


Reads files from a HDFS directory, where each discrete file will be consumed as
a single message payload.

```yaml
# Config fields, showing default values
input:
  hdfs:
    hosts:
      - localhost:9000
    user: benthos_hdfs
    directory: ""
```

### Metadata

This input adds the following metadata fields to each message:

``` text
- hdfs_name
- hdfs_path
```

You can access these metadata fields using
[function interpolation](/docs/configuration/interpolation#metadata).

## Fields

### `hosts`

A list of target host addresses to connect to.


Type: `array`  
Default: `["localhost:9000"]`  

### `user`

A user ID to connect as.


Type: `string`  
Default: `"benthos_hdfs"`  

### `directory`

The directory to consume from.


Type: `string`  
Default: `""`  

