---
layout: post
title: "Bunny 2.11.0 is released"
date: 2018-06-24 00:01
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.11.0](https://rubygems.org/gems/bunny/versions/2.11.0) is released to rubygems.org.

`2.11.0` and `2.10.0` are minor releases that include **minor potentially breaking changes**.
Only a small number of applications is affected.



## Changes between Bunny 2.10.0 and 2.11.0 (Jun 21st, 2018)

### More Reliable System-wide Trusted Certificate Directory Detection

Bunny no longer tries to compile a list of trusted CA certificates on its own.
Instead it uses an OpenSSL API method that makes OpenSSL set the path(s),
which should cover more platforms and be forward- and backward-compatible.

GitHub issue: [#555](https://github.com/ruby-amqp/bunny/issues/555).

Contributed by Ana María Martínez Gómez.




## Changes between Bunny 2.9.0 and 2.10.0 (Jun 5th, 2018)

`2.10.0` is a maintenance release that introduces a couple of
.

### Disabling Heartbeats Also Disables TCP Socket Read Timeouts

Disabling heartbeats will now disable TCP socket read timeouts.

They go hand in hand and users who prefer TCP keepalives via
kernel configuration previously had to also explicitly configure
a zero read timeout.

GitHub issue: [#551](https://github.com/ruby-amqp/bunny/pull/551).

Contributed by Carl Hörberg.


### `verify_peer: false` Has the Expected Effect Again

Make sure `verify_peer: false` has the expected effect again.

Default value of connection's `:verify_peer` option to `true` only when
all of `:verify_ssl`, `:verify_peer`, and `:verify` are `nil`.

GitHub issue: [#541](https://github.com/ruby-amqp/bunny/issues/541).

Contributed by Howard Ding.


### Maximum Number of Channels Limited to 2K by Default

Default maximum number of channels is limited to 2047 to reduce the probability
of severe channel leaks. See [rabbitmq/rabbitmq-server#1593](https://github.com/rabbitmq/rabbitmq-server/issues/1593) for details.

Applications that want to use more channels per connection can still configure a higher value
using the `channel_max` setting (for both Bunny and RabbitMQ server).

GitHub issue: [#553](https://github.com/ruby-amqp/bunny/pull/553).


### Squashed Some Warnings

GitHub issue: [#552](https://github.com/ruby-amqp/bunny/pull/552).

Contributed by @utilum.



### Disabling Heartbeats Disables TCP Socket Read Timeouts

Disabling heartbeats will also disable TCP socket read timeouts,
since the two are effectively interconnected. In this case a mechanism
such as [TCP keepalives](http://www.rabbitmq.com/heartbeats.html#tcp-keepalives) is assumed to be used.

See [RabbitMQ heartbeats guide](http://www.rabbitmq.com/heartbeats.html) for a more
detailed overview of the options.

GH issue: [#519](https://github.com/ruby-amqp/bunny/issues/519).

Contributed by Carl Hörberg.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.11.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
