---
layout: post
title: "'Bunny 0.9.0.pre6 is released'"
date: 2013-01-14 19:19
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre6](https://rubygems.org/gems/bunny/versions/0.9.0.pre6) is released to rubygems.org.

This release includes one major feature and a few bug fixes. It is 100% backwards
compatible.


## Highlights

The major feature is automatic network failure recovery. This includes recovery of
exchanges, queues, bindings and consumers that were declared/added on the
recovered Bunny connection.

In addition, documentation guides on error handling and recovery is now [up online](http://rubybunny.info/articles/error_handling.html).


## Change Log

### Automatic Network Failure Recovery

Automatic Network Failure Recovery is a new Bunny feature that was earlier
impemented and vetted out in [amqp gem](http://rubyamqp.info). What it does
is, when a network activity loop detects an issue, it will try to
periodically recover [first TCP, then] AMQP 0.9.1 connection, reopen
all channels, recover all exchanges, queues, bindings and consumers
on those channels (to be clear: this only includes entities and consumers added via
Bunny).

Publishers and consumers will continue operating shortly after the network
connection recovers.

Learn more in the [Error Handling and Recovery](http://rubybunny.info/articles/error_handling.html)
documentation guide.

### Confirms Listeners

Bunny now supports listeners (callbacks) on

``` ruby
ch.confirm_select do |delivery_tag, multiple, nack|
  # handle confirms (e.g. perform retries) here
end
```

Contributed by Greg Brockman.

### Publisher Confirms Improvements

Publisher confirms implementation now uses non-strict equality (`<=`) for
cases when multiple messages are confirmed by RabbitMQ at once.

`Bunny::Channel#unconfirmed_set` is now part of the public API that lets
developers access unconfirmed delivery tags to perform retries and such.

Contributed by Greg Brockman.

### Publisher Confirms Concurrency Fix

`Bunny::Channel#wait_for_confirms` will now correctly block the calling
thread until all pending confirms are received.

Change log is [available on GitHub](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md#changes-between-bunny-090pre5-and-090pre6).


## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Make network failure recovery configurable
 * Bring back TLS support
 * Add logging
 * API reference documentation

Chances are, the next release will be RC1.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
