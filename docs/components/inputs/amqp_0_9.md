---
title: amqp_0_9
type: input
status: stable
categories: ["Services"]
---

<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the contents of:
     lib/input/amqp_0_9.go
-->

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';


Connects to an AMQP (0.91) queue. AMQP is a messaging protocol used by various
message brokers, including RabbitMQ.


<Tabs defaultValue="common" values={[
  { label: 'Common', value: 'common', },
  { label: 'Advanced', value: 'advanced', },
]}>

<TabItem value="common">

```yaml
# Common config fields, showing default values
input:
  amqp_0_9:
    url: amqp://guest:guest@localhost:5672/
    queue: benthos-queue
    consumer_tag: benthos-consumer
    prefetch_count: 10
```

</TabItem>
<TabItem value="advanced">

```yaml
# All config fields, showing default values
input:
  amqp_0_9:
    url: amqp://guest:guest@localhost:5672/
    queue: benthos-queue
    queue_declare:
      durable: true
      enabled: false
    bindings_declare: []
    consumer_tag: benthos-consumer
    auto_ack: false
    prefetch_count: 10
    prefetch_size: 0
    tls:
      enabled: false
      skip_cert_verify: false
      root_cas_file: ""
      client_certs: []
```

</TabItem>
</Tabs>

TLS is automatic when connecting to an `amqps` URL, but custom
settings can be enabled in the `tls` section.

### Metadata

This input adds the following metadata fields to each message:

``` text
- amqp_content_type
- amqp_content_encoding
- amqp_delivery_mode
- amqp_priority
- amqp_correlation_id
- amqp_reply_to
- amqp_expiration
- amqp_message_id
- amqp_timestamp
- amqp_type
- amqp_user_id
- amqp_app_id
- amqp_consumer_tag
- amqp_delivery_tag
- amqp_redelivered
- amqp_exchange
- amqp_routing_key
- All existing message headers, including nested headers prefixed with the key of their respective parent.
```

You can access these metadata fields using
[function interpolation](/docs/configuration/interpolation#metadata).

## Fields

### `url`

A URL to connect to.


Type: `string`  
Default: `"amqp://guest:guest@localhost:5672/"`  

```yaml
# Examples

url: amqp://localhost:5672/

url: amqps://guest:guest@localhost:5672/
```

### `queue`

An AMQP queue to consume from.


Type: `string`  
Default: `"benthos-queue"`  

### `queue_declare`

Allows you to passively declare the target queue. If the queue already exists
then the declaration passively verifies that they match the target fields.


Type: `object`  
Default: `{"durable":true,"enabled":false}`  

```yaml
# Examples

queue_declare:
  durable: false
  enabled: true
```

### `bindings_declare`

Allows you to passively declare bindings for the target queue.


Type: `array`  
Default: `[]`  

```yaml
# Examples

bindings_declare:
  - exchange: foo
    key: bar
```

### `consumer_tag`

A consumer tag.


Type: `string`  
Default: `"benthos-consumer"`  

### `auto_ack`

Acknowledge messages automatically as they are consumed rather than waiting for acknowledgments from downstream. This can improve throughput and prevent the pipeline from blocking but at the cost of eliminating delivery guarantees.


Type: `bool`  
Default: `false`  

### `prefetch_count`

The maximum number of pending messages to have consumed at a time.


Type: `number`  
Default: `10`  

### `prefetch_size`

The maximum amount of pending messages measured in bytes to have consumed at a time.


Type: `number`  
Default: `0`  

### `tls`

Custom TLS settings can be used to override system defaults.


Type: `object`  

### `tls.enabled`

Whether custom TLS settings are enabled.


Type: `bool`  
Default: `false`  

### `tls.skip_cert_verify`

Whether to skip server side certificate verification.


Type: `bool`  
Default: `false`  

### `tls.root_cas_file`

An optional path of a root certificate authority file to use. This is a file, often with a .pem extension, containing a certificate chain from the parent trusted root certificate, to possible intermediate signing certificates, to the host certificate.


Type: `string`  
Default: `""`  

```yaml
# Examples

root_cas_file: ./root_cas.pem
```

### `tls.client_certs`

A list of client certificates to use. For each certificate either the fields `cert` and `key`, or `cert_file` and `key_file` should be specified, but not both.


Type: `array`  

```yaml
# Examples

client_certs:
  - cert: foo
    key: bar

client_certs:
  - cert_file: ./example.pem
    key_file: ./example.key
```

### `tls.client_certs[].cert`

A plain text certificate to use.


Type: `string`  
Default: `""`  

### `tls.client_certs[].key`

A plain text certificate key to use.


Type: `string`  
Default: `""`  

### `tls.client_certs[].cert_file`

The path to a certificate to use.


Type: `string`  
Default: `""`  

### `tls.client_certs[].key_file`

The path of a certificate key to use.


Type: `string`  
Default: `""`  

