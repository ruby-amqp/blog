---
layout: post
title: "Bunny 0.9.0.pre7 is released"
date: 2013-02-12 19:41
comments: false
categories: 
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre7](https://rubygems.org/gems/bunny/versions/0.9.0.pre7) is released to rubygems.org.

This release consists of bug fixes and (very) minor features. It is 100% backwards
compatible.


## Highlights

This release includes a number of bug fixes and (very) minor features plus
API reference.


## Change Log

### Bunny::Channel#on_error

`Bunny::Channel#on_error` is a new method that lets you define
handlers for channel errors that are caused by methods that have no
responses in the protocol (`basic.ack`, `basic.reject`, and `basic.nack`).

This is rarely necessary but helps make sure no error goes unnoticed.

Example:

``` ruby
channel.on_error |ch, channel_close|
  puts channel_close.inspect
end
```

### Fixed Framing of Larger Messages With Unicode Characters

Larger (over 128K) messages with non-ASCII characters are now always encoded
correctly with amq-protocol `1.2.0`.


### Efficiency Improvements

Publishing of large messages is now done more efficiently.

Contributed by Greg Brockman.


### API Reference

[Bunny API reference](http://reference.rubybunny.info) is now up online.


### Bunny::Channel#basic_publish Support For :persistent

`Bunny::Channel#basic_publish` now supports both
`:delivery_mode` and `:persistent` options.

### Bunny::Channel#nacked_set

`Bunny::Channel#nacked_set` is a counter-part to `Bunny::Channel#unacked_set`
that contains `basic.nack`-ed (rejected) delivery tags.



## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Make network failure recovery configurable
 * Bring back TLS support
 * Add logging



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
