---
layout: post
title: "Bunny 0.9.0.pre8 is released"
date: 2013-03-12 23:37
comments: false
categories: 
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre8](https://rubygems.org/gems/bunny/versions/0.9.0.pre8) is released to rubygems.org.

This release has bug fixes and (very) minor features. It is 100% backwards
compatible.


## Changes between Bunny 0.9.0.pre7 and 0.9.0.pre8

### Stability Improvements

Several stability improvements in the network
layer, connection error handling, and concurrency hazards.


### Automatic Connection Recovery Can Be Disabled

Automatic connection recovery now can be disabled by passing
the `:automatically_recover => false` option to `Bunny#initialize`).

When the recovery is disabled, network I/O-related exceptions will
cause an exception to be raised in thee thread the connection was
started on.


### No Timeout Control For Publishing

`Bunny::Exchange#publish` and `Bunny::Channel#basic_publish` no
longer perform timeout control (using the timeout module) which
roughly increases throughput for flood publishing by 350%.

Apps that need delivery guarantees should use publisher confirms.



## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Add logging
 * Finish TLS support
 * Make network failure recovery even more flexible



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
