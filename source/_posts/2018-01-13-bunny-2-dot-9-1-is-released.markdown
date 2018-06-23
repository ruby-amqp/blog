---
layout: post
title: "Bunny 2.9.1 is released"
date: 2018-01-13 01:45
comments: true
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.9.1](https://rubygems.org/gems/bunny/versions/2.9.1) is released to rubygems.org.

`2.9.1` is a minor feature release that drops support for Ruby 2.2 and earlier.



## Changes between Bunny 2.9.0 and 2.9.1 (Jan 11th, 2018)

### Default CA Certificate Paths are Respected Again

GitHub issue: [#539](https://github.com/ruby-amqp/bunny/issues/539).

Contributed by Carl Hörberg.


## Changes between Bunny 2.8.0 and 2.9.0 (Jan 8th, 2018)

### Ruby 2.2 Requirement

Bunny now requires Ruby 2.2.


### Support for Additional URI Query Parameters

GitHub issue: [#534](https://github.com/ruby-amqp/bunny/pull/534).

Contributed by Andrew Babichev.


## Changes between Bunny 2.7.0 and 2.8.0 (Dec 18th, 2018)

This release has **minor breaking public API changes**.

### `Bunny::Channel#close` on a Closed Channel Now Raises a Sensible Exception

`Bunny::Channel#close` on an already closed channel will now raise a sensible exception.
If the channel was closed due to a channel-level protocol exception, that exception will
be mentioned.

GitHub issue: [#528](https://github.com/ruby-amqp/bunny/issues/528), see [9df7cb](https://github.com/ruby-amqp/bunny/commit/9df7cb04d9ff12b1af62a11e239fd81e5472c872) for
details.

### JRuby 9K Compatibility

A JRuby 9K compatibility issue was corrected by Marian Posăceanu.
Note that JRuby users are recommended to use [March Hare](http://rubymarchhare.info/), a JRuby-oriented client, instead
of Bunny.

GitHub issue: [#529](https://github.com/ruby-amqp/bunny/pull/529)

### Connection Exceptions are Logged as Warning with Automatic Recovery

When automatic recovery is enabled, connection errors are now logged as warnings
and not errors.

Contributed by Merten Falk.

GitHub issue: [#531](https://github.com/ruby-amqp/bunny/pull/531)

### Server Heartbeat Value as a String

It is now possible to specify a server-defined heartbeat value as a string (`"server"`), not just
a symbol. This makes it easier to load settings from YAML files.

Contributed by Tyrone Wilson.

GitHub issue: [#524](https://github.com/ruby-amqp/bunny/pull/524)


## Changes between Bunny 2.7.0 and 2.7.1 (Sep 25th, 2017)

### Sensible Socket Read Timeouts When RabbitMQ is Configured to Disabled Heartbeats

Bunny now correctly handles scenarios where server is configured
to disable heartbeats (which is a terrible idea, don't do it!)

GitHub issue: [#519](https://github.com/ruby-amqp/bunny/issues/519).

### Bunny::Channel#basic_get Usability

`Bunny::Channel#basic_get` invoked with a non-existent queue now
throws a channel exception instead of a generic operation timeout.

GitHub issue: [#518](https://github.com/ruby-amqp/bunny/issues/518).

### Spec Suite Improvements

`BUNNY_CERTIFICATE_DIR` environment variable now can be used
to override local CA and client certificate/key pair directory.
The directory is expected to be the result directory generated
by the basic [tls-gen](http://github.com/michaelklishin/tls-gen) profile.

TLSv1.0 is no longer used in tests because it's being disabled by default
by more and more installations as it has known vulnerabilities
and is no longer considered to be acceptable by several compliance
standards (e.g. PCI DSS).

### Improved Synchronisation for channel.close Handlers

`channel.close` handler will now acquire a lock . This avoids concurrency
hazards in some rare scenarios when a channel is closed due a protocol
exception by the server and concurrently opened by user code
at the same time.

### More Meaningful Error Messages in Bunny::Session#create_channel

Sometimes users attempt to open a channel on a connection that
isn't connected yet because `Bunny::Session#start` was never invoked.

`Bunny::Session#create_channel` will now provide a more sensible exception message
in those cases.




## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.9.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
