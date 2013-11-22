---
layout: post
title: "RabbitMQ HTTP API client 0.9.0 is Released"
date: 2013-11-22 13:23
comments: false
categories:
  - rabbitmq_http_api_client
  - releases
---

Ruby RabbitMQ HTTP API client `0.9.0` is released.

This is a minor feature release.

## Changes Between 0.8.0 and 0.9.0

### New Queue Binding Methods

`RabbitMQ::HTTP::Client#queue_binding_info`,
`RabbitMQ::HTTP::Client#bind_queue`, and
`RabbitMQ::HTTP::Client#delete_queue_binding`
are new methods that operate on queue bindings:

``` ruby
c = RabbitMQ::HTTP::Client.new("http://guest:guest@127.0.0.1:15672")

c.bind_queue("/", "a.queue", "an.exchange", "routing.key")
c.queue_binding_info("/", "a.queue", "an.exchange", "properties.key")
c.delete_queue_binding("/", "a.queue", "an.exchange", "properties.key")
```

Contributed by Noah Magram.


## Changes Between 0.7.0 and 0.8.0

### Client#protocol_ports

`RabbitMQ::HTTP::Client#enabled_protocols` is a new method that returns
a hash of enabled protocols to their ports. The keys are the same as
returned by `Client#enabled_protocols`:

``` ruby
# when TLS and MQTT plugin is enabled
c.protocol_ports # => {"amqp" => 5672, "amqp/ssl" => 5671, "mqtt" => 1883}
```

### Client#enabled_protocols

`RabbitMQ::HTTP::Client#enabled_protocols` is a new method that returns
a list of enabled protocols. Some common values are:

 * `amqp` (AMQP 0-9-1)
 * `amqp/ssl` (AMQP 0-9-1 with TLS enabled)
 * `mqtt`
 * `stomp`

``` ruby
# when TLS and MQTT plugin is enabled
c.enabled_protocols # => ["amqp", "amqp/ssl", "mqtt"]
```

[Full change log](https://github.com/ruby-amqp/rabbitmq_http_api_client/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
