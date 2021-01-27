---
title: select_parts
type: processor
status: stable
categories: ["Utility"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/processor/select_parts.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


Cherry pick a set of messages from a batch by their index. Indexes larger than
the number of messages are simply ignored.


<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

<TabItem value="common">

```yaml
# Common config fields, showing default values
select_parts: {}
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
select_parts:
  parts:
    - 0
```

</TabItem>
</Tabs>

The selected parts are added to the new message batch in the same order as the
selection array. E.g. with 'parts' set to [ 2, 0, 1 ] and the message parts
[ '0', '1', '2', '3' ], the output will be [ '2', '0', '1' ].

If none of the selected parts exist in the input batch (resulting in an empty
output message) the batch is dropped entirely.

Message indexes can be negative, and if so the part will be selected from the
end counting backwards starting from -1. E.g. if index = -1 then the selected
part will be the last part of the message, if index = -2 then the part before
the last element with be selected, and so on.

The functionality of this processor depends on being applied across messages
that are batched. You can find out more about batching [in this doc](/docs/configuration/batching).

## Fields

### `parts`

An optional array of message indexes of a batch that the processor should apply to.
If left empty all messages are processed. This field is only applicable when
batching messages [at the input level](/docs/configuration/batching).

Indexes can be negative, and if so the part will be selected from the end
counting backwards starting from -1.


Type: `array`  
Default: `[0]`  

