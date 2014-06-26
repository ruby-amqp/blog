---
layout: post
title: "RabbitMQ HTTP API client 1.2.0 is Released"
date: 2014-06-26 08:44
comments: false
categories:
  - rabbitmq_http_api_client
  - releases
---

Ruby RabbitMQ HTTP API client `1.2.0` is released.

This release restores Ruby 1.8 compatibility.

## Changes Between 1.1.0 and 1.2.0

### Ruby 1.8 Compatibility Restored

The library no longer uses 1.9-specific hash syntax.



## Changes Between 1.0.0 and 1.1.0

### declare_exchange

It is now possible to declare an exchange over HTTP API using `RabbitMQ::HTTP::Client#declare_exchange`:

``` ruby
c.declare_exchange("/", exchange_name, :durable => false, :type => "fanout")
```

Contributed by Jake Davis (Simple).


## Changes Between 0.9.0 and 1.0.0

### Hashi Upgrade

The library now depends on `hashie ~> 2.0.5`.

### Faraday Upgrade

The library now depends on `faraday ~> 0.8.9`.


## Change Log

[Full change log](https://github.com/ruby-amqp/rabbitmq_http_api_client/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
