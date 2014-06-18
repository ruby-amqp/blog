---
layout: post
title: "Bunny 1.3.0 is released"
date: 2014-06-18 17:55
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.3.0](https://rubygems.org/gems/bunny/versions/1.3.0) is released to rubygems.org.

This is a minor feature and bug fix release.


## Changes between Bunny 1.3.0 and 1.2.0

### TLS Can Be Explicitly Disabled

TLS now can be explicitly disabled even when connecting (without TLS)
to the default RabbitMQ TLS/amqps port (5671):

``` ruby
conn = Bunny.new(:port => 5671, :tls => false)
```

Contributed by Muhan Zou.


### Single Threaded Connections Raise Shutdown Exceptions

Single threaded Bunny connections will now raise exceptions
that occur during shutdown as is (instead of trying to shut down
I/O loop which only threaded ones have).

Contributed by Carl Hörberg.


### Synchronization Improvements for Session#close

`Bunny::Session#close` now better synchronizes state transitions,
eliminating a few race condition scenarios with I/O reader thread.


### Bunny::Exchange.default Fix

`Bunny::Exchange.default` no longer raises an exception.

Note that it is a legacy compatibility method. Please use
`Bunny::Channel#default_exchange` instead.

Contributed by Justin Litchfield.

GH issue [#211](https://github.com/ruby-amqp/bunny/pull/211).

### Bunny::Queue#pop_as_hash Removed

`Bunny::Queue#pop_as_hash`, which was added to ease migration
to Bunny 0.9, was removed.

### Bunny::Queue#pop Wraps Metadata

`Bunny::Queue#pop` now wraps `basic.get-ok` and message properties
into `Bunny::GetResponse` and `Bunny::MessageProperties`, just like
`basic.consume` deliveries.

GH issue: [#212](https://github.com/ruby-amqp/bunny/issues/212).

### Better Synchronization for Publisher Confirms

Publisher confirms implementation now synchronizes unconfirmed
set better.

Contributed by Nicolas Viennot.

### Channel Allocation After Recovery

Channel id allocator is no longer reset after recovery
if there are channels open. Makes it possible to open channels
on a recovered connection (in addition to the channels
it already had).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
