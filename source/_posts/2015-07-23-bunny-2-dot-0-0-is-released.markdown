---
layout: post
title: "Bunny 2.0.0 is released"
date: 2015-07-23 12:55
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.0.0](https://rubygems.org/gems/bunny/versions/2.0.0) is released to rubygems.org.

2.0.0 is a minor feature and bug fix release that drops Ruby 1.9 and 1.8 support.


## Changes between Bunny 1.7.0 and 2.0.0

Bunny `2.0` doesn't have any breaking API changes
but drops Ruby 1.8 and 1.9 (both EOL'ed) support,
hence the version.

### Minimum Required Ruby Version is 2.0

Bunny `2.0` requires Ruby 2.0 or later.

## Non-Blocking Writes

Bunny now uses non-blocking socket writes, uses a reduced
number of writes for message publishing (frames are batched
into a single write), and handles TCP back pressure from
RabbitMQ better.

Contributed by Irina Bednova and Michael Klishin.

### Reduced Timeout Use

`Bunny::ContinuationQueue#poll` no longer relies on Ruby's `Timeout` which has
numerous issues, including starting a new "interruptor" thread per operation,
which is far from efficient.

Contributed by Joe Eli McIlvain and Carl Hörberg.

### Capped Number of Connection Recovery Attempts

`:recovery_attempts` is a new option that limits the number of
connection recovery attempts performed by Bunny. `nil` means
"no limit".

Contributed by Irina Bednova.

### Bunny::Channel#basic_ack and Related Methods Improvements

`Bunny::Channel#basic_ack`, `Bunny::Channel#basic_nack`, and `Bunny::Channel#basic_reject`
now adjust delivery tags between connection recoveries, as well as have a default value for
the second argument.

Contributed by Wayne Conrad.

### Logger Output Remains Consistent

Setting the `@logger.progname` attribute changes the output of the logger.
This is not expected behaviour when the client provides a custom logger.
Behaviour remains unchainged when the internally initialized logger is used.

Contributed by Justin Carter.

### prefetch_count is Limited to 65535

Since `basic.qos`'s `prefetch_count` field is of type `short` in the protocol,
Bunny must enforce its maximum allowed value to `2^16 - 1` to avoid
confusing issues due to overflow.

### Per-Consumer and Per-Channel Prefetch

Recent RabbitMQ versions support `basic.qos` `global` flag, controlling whether
`prefetch` applies per-consumer or per-channel. Bunny `Channel#prefetch` now
allows flag to be set as optional parameter, with the same default behaviour as
before (per-consumer).

Contributed by tiredpixel.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.

## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.

