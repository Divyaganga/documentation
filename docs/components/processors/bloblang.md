---
title: bloblang
type: processor
status: stable
categories: ["Mapping","Parsing"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/processor/bloblang.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


Executes a [Bloblang](/docs/guides/bloblang/about) mapping on messages.

```yaml
# Config fields, showing default values
bloblang: ""
```

Bloblang is a powerful language that enables a wide range of mapping,
transformation and filtering tasks. For more information
[check out the docs](/docs/guides/bloblang/about).

## Examples

<Tabs defaultValue="Mapping" values={[
{ label: 'Mapping', value: 'Mapping', },
{ label: 'More Mapping', value: 'More Mapping', },
]}>

<TabItem value="Mapping">


Given JSON documents containing an array of fans:

```json
{
  "id":"foo",
  "description":"a show about foo",
  "fans":[
    {"name":"bev","obsession":0.57},
    {"name":"grace","obsession":0.21},
    {"name":"ali","obsession":0.89},
    {"name":"vic","obsession":0.43}
  ]
}
```

We can reduce the fans to only those with an obsession score above 0.5, giving us:

```json
{
  "id":"foo",
  "description":"a show about foo",
  "fans":[
    {"name":"bev","obsession":0.57},
    {"name":"ali","obsession":0.89}
  ]
}
```

With the following config:

```yaml
pipeline:
  processors:
  - bloblang: |
      root = this
      fans = fans.map_each(match {
        this.obsession > 0.5 => this
        _ => deleted()
      })
```

</TabItem>
<TabItem value="More Mapping">


When receiving JSON documents of the form:

```json
{
  "locations": [
    {"name": "Seattle", "state": "WA"},
    {"name": "New York", "state": "NY"},
    {"name": "Bellevue", "state": "WA"},
    {"name": "Olympia", "state": "WA"}
  ]
}
```

We could collapse the location names from the state of Washington into a field `Cities`:

```json
{"Cities": "Bellevue, Olympia, Seattle"}
```

With the following config:

```yaml
pipeline:
  processors:
    - bloblang: '{"Cities":this.locations.filter(this.state == "WA").map_each(this.name).sort().join(", ")}'
```

</TabItem>
</Tabs>

## Error Handling

Bloblang mappings can fail, in which case the message remains unchanged, errors
are logged, and the message is flagged as having failed, allowing you to use
[standard processor error handling patterns](/docs/configuration/error_handling).

However, Bloblang itself also provides powerful ways of ensuring your mappings
do not fail by specifying desired fallback behaviour, which you can read about
[in this section](/docs/guides/bloblang/about#error-handling).
