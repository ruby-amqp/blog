---
layout: post
title: "Bunny 1.2.0 is released"
date: 2014-04-09 14:19
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.2.0](https://rubygems.org/gems/bunny/versions/1.2.0) is released to rubygems.org.

This is a minor feature and bug fix release.


## Changes between Bunny 1.1.0 and 1.2.0

### :key Supported in Bunny::Channel#queue_bind

It is now possible to use `:key` (which Bunny versions prior to 0.9 used)
as well as `:routing_key` as an argument to `Bunny::Queue#bind`.

### System Exceptions Not Rescued by the Library

Bunny now rescues `StandardError` instead of `Exception` where
it automatically does so (e.g. when dispatching deliveries to consumers).

Contributed by Alex Young.


### Initial Socket Connection Timeout Again Raises Bunny::TCPConnectionFailed

Initial socket connection timeout again raises `Bunny::TCPConnectionFailed`
on the connection origin thread.

### Thread Leaks Plugged

`Bunny::Session#close` on connections that have experienced a network failure
will correctly clean up I/O and heartbeat sender threads.

Contributed by m-o-e.

### Bunny::Concurrent::ContinuationQueue#poll Rounding Fix

`Bunny::Concurrent::ContinuationQueue#poll` no longer floors the argument
to the nearest second.

Contributed by Brian Abreu.

### Routing Key Limit

Per AMQP 0-9-1 spec, routing keys cannot be longer than 255 characters.
`Bunny::Channel#basic_publish` and `Bunny::Exchange#publish` now enforces
this limit.

### Nagle's Algorithm Disabled Correctly

Bunny now properly disables [Nagle's algorithm](http://boundary.com/blog/2012/05/02/know-a-delay-nagles-algorithm-and-you/)
on the sockets it opens. This likely means
significantly lower latency for workloads that involve
sending a lot of small messages very frequently.

[Contributed](https://github.com/ruby-amqp/bunny/pull/187) by Nelson Gauthier (AirBnB).

### Internal Exchanges

Exchanges now can be declared as internal:

``` ruby
ch = conn.create_channel
x  = ch.fanout("bunny.tests.exchanges.internal", :internal => true)
```

Internal exchanges cannot be published to by clients and are solely used
for [Exchange-to-Exchange bindings](http://rabbitmq.com/e2e.html) and various
plugins but apps may still need to bind them. Now it is possible
to do so with Bunny.

### Uncaught Consumer Exceptions

Uncaught consumer exceptions are now handled by uncaught exceptions
handler that can be defined per channel:

``` ruby
ch.on_uncaught_exception do |e, consumer|
  # ...
end
```


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.2.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
