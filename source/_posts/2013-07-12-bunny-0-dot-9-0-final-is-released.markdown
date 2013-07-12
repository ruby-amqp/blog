---
layout: post
title: "Bunny 0.9.0 final is released"
date: 2013-07-12 15:00
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0](https://rubygems.org/gems/bunny/versions/0.9.0) is released to rubygems.org.

This release is a ground-up rewrite of Bunny that eliminates a lot of limitations
of earlier versions, adds new features, improves throughput, makes Bunny benefit
from runtime parallelism on Ruby implementations that support it and introduces
other numerous improvements.

It is **not entirely backwards compatible**, although we've tried hard to make upgrading
as seamless as possible.

This is a major step forward for Bunny. The library is now a feature complete,
first class RabbitMQ client.

We encourage all Bunny users to upgrade to it.


## Release Highlights

### Feature Complete

Bunny 0.9 supports all RabbitMQ 3.x features, including [extensions](http://www.rabbitmq.com/extensions.html).

If something is possible to do with RabbitMQ over AMQP 0.9.1, you can do it with Bunny 0.9.


### No More Limitations

Bunny `0.7.x` and `0.8.0` did not support publishing of messages over 128 Kb in size and
had limitations around asynchronous ("push") consumers.

None of these limitations exist in 0.9.


### Error Handling and Recovery

Bunny 0.9 introduces automatic [recovery from network
failures](http://rubybunny.info/articles/error_handling.html), much
like amqp gem has.


## Better Performance

Bunny 0.9 uses the same protocol serialization library as amqp gem. It has lower memory footprint
and significantly more efficient: serialization throughput increased from 20% to x50 times
compared to Bunny 0.8 serialization code.

Fewer memory allocations mean less GC stress and GC-induced CPU burn.


### Concurrency

Bunny uses a separate thread for network activity. Consumers dispatch messages to a thread pool
(by default of size 1) that can be tuned.

On Ruby runtimes that support runtime parallelism, this will increase throughput of both
consumers and publishers on multicore hardware.


### Improved Documentation

Bunny now has [documentation guides](http://rubybunny.info) that are on par or even better
than [amqp gem documentation](http://rubyamqp.info).


### Imprved TLS Support

Bunny's [TLS/SSL support](http://rubybunny.info/articles/tls.html) is more flexible: more options available to configure when you need
them.


### RabbitMQ 2.x is the Minimum Supported Version

RabbitMQ 2.x is now the minimum supported version. 3.x releases are recommended.



## Full Bunny 0.9 Change Log

[Detailed Bunny changelog](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) is available on
GitHub.



## Documentation

### Guides

[Documentation guides](http://rubybunny.info):

 * [Getting Started](http://rubybunny.info/articles/getting_started.html)
 * [Concepts and Terminology](http://www.rabbitmq.com/tutorials/amqp-concepts.html)
 * [Connecting to RabbitMQ](http://rubybunny.info/articles/connecting.html)
 * [Queues and Consumers](http://rubybunny.info/articles/queues.html)
 * [Exchanges and Publishers](http://rubybunny.info/articles/exchanges.html)
 * [Bindings](http://rubybunny.info/articles/bindings.html)
 * [Durability and Related Matters](http://rubybunny.info/articles/durability.html)
 * [Using AMQP 0.9.1 Extensions in RabbitMQ](http://rubybunny.info/articles/extensions.html)
 * [Error Handling and Recovery](http://rubybunny.info/articles/error_handling.html)
 * [Using TLS/SSL Connections](http://rubybunny.info/articles/tls.html)
 * [Troubleshooting](http://rubybunny.info/articles/troubleshooting.html)

#### API Reference

 * [API reference](http://reference.rubybunny.info)


## Getting Help & Reporting Issues




## Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
