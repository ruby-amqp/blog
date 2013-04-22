---
layout: post
title: "Bunny 0.9.0.pre9 is released"
date: 2013-04-22 12:46
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre9](https://rubygems.org/gems/bunny/versions/0.9.0.pre9) is released to rubygems.org.

This is a bug fix release. It is 100% backwards compatible.


## Changes between Bunny 0.9.0.pre8 and 0.9.0.pre9

Most of the work in this release has gone into investigating and fixing issues that manifested
in a [high CPU usage spike](https://github.com/ruby-amqp/bunny/issues/95). In some cases,
the issue turned out to be system-specific (e.g. a leap second bug that affected certain
kernels and environments such as OpenVZ).


### More Reliable Heartbeat Sender

Heartbeat sender no longer slips into an infinite loop if it encounters an exception.
Instead, it will just stop (and presumably re-started when the network error recovery
kicks in or the app reconnects manually).


### Network Recovery After Delay

Network reconnection now kicks in after a delay to avoid aggressive
reconnections in situations when we don't want to endlessly reconnect
(e.g. when the connection was closed via the Management UI).

The `:network_recovery_interval` option passed to `Bunny::Session#initialize` and `Bunny.new`
controls the interval. Default is 5 seconds.


### Default Heartbeat Value Is Now Server-Defined

Bunny will now use heartbeat value provided by RabbitMQ by default.




## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Add logging
 * Finish TLS support
 * Make network failure recovery even more flexible



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
