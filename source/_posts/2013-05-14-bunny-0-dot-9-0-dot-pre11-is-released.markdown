---
layout: post
title: "Bunny 0.9.0.pre11 is released"
date: 2013-05-14 15:59
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre10](https://rubygems.org/gems/bunny/versions/0.9.0.pre10) is released to rubygems.org.

This release includes minor new features, stability and performance improvements. It is **backwards compatible**.


## Changes between Bunny 0.9.0.pre10 and 0.9.0.pre11

### Bunny::Session#create_channel Now Accepts Consumer Work Pool Size

`Bunny::Session#create_channel` now accepts consumer work pool size as
the second argument:

``` ruby
# nil means channel id will be allocated by Bunny.
# 8 is the number of threads in the consumer work pool this channel will use.
ch = conn.create_channel(nil, 8)
```

### Heartbeat Fix For Long Running Consumers

Long running consumers that don't send any data will no longer
suffer from connections closed by RabbitMQ because of skipped
heartbeats.

Activity tracking now takes sent frames into account.


### Time-bound continuations

If a network loop exception causes "main" session thread to never
receive a response, methods such as `Bunny::Channel#queue` will simply time out
and raise Timeout::Error now, which can be handled.

It will not start automatic recovery for two reasons:

 * It will be started in the network activity loop anyway
 * It may do more damage than good

Kicking off network recovery manually is a matter of calling
`Bunny::Session#handle_network_failure`.

The main benefit of this implementation is that it will never
block the main app/session thread forever, and it is really
efficient on JRuby thanks to a j.u.c. blocking queue.

Fixes #112.


### Logging Support

Every Bunny connection now has a logger. By default, Bunny will use STDOUT
as logging device. This is configurable using the `:log_file` option:

``` ruby
require "bunny"

conn = Bunny.new(:log_level => :warn)
```

or the `BUNNY_LOG_LEVEL` environment variable that can take one of the following
values:

 * `debug` (very verbose)
 * `info`
 * `warn`
 * `error`
 * `fatal` (least verbose)

Severity is set to `warn` by default. To disable logging completely, set the level
to `fatal`.

To redirect logging to a file or any other object that can act as an I/O entity,
pass it to the `:log_file` option.


### Publishing Performance Improvements

Publishing throughput has been improved by about 10% for messages smaller
than `128K`. The gains are more substantial on JRuby: improved implementation
is easier for JVM to inline.



## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Fix any remaining important issues we get reports for
 * Finish TLS support



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
