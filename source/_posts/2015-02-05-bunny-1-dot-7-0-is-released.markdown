---
layout: post
title: "Bunny 1.7.0 is released"
date: 2015-02-05 11:45
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.7.0](https://rubygems.org/gems/bunny/versions/1.7.0) is released to rubygems.org.

1.7.0 is a minor feature release.


## Changes between Bunny 1.6.0 and 1.7.0

### TLS Peer Verification Enabled by Default

When using TLS, peer verification is now enabled by default.
It is still possible to [disable verification](http://rubybunny.info/articles/tls.html), e.g. for convenient
development locally.

Peer verification is a means of protection against man-in-the-middle attacks
and is highly recommended in production settings. However, it can be an inconvenience
during local development. We believe it's time to have the default to be
more secure.

Contributed by Michael Klishin (Pivotal) and Andre Foeken (Nedap).


### Higher Default Connection Timeout

Default connection timeout has been increased to 25 seconds. The older
default of 5 seconds wasn't sufficient in some edge cases with DNS
resolution (e.g. when primary DNS server is down).

The value can be overriden at connection time.

Contributed by Yury Batenko.


### Socket Read Timeout No Longer Set to 0 With Disabled Heartbeats

GH issue: [#267](https://github.com/ruby-amqp/bunny/pull/267).


### JRuby Writes Fixes

On JRuby, Bunny reverts back to using plain old `write(2)` for writes. The CRuby implementation
on JRuby suffers from I/O incompatibilities. Until JRuby

Bunny users who run on JRuby are highly recommended to switch to [March Hare](http://rubymarchhare.info),
which has nearly identical API and is significantly more efficient.


### Bunny::Session#with_channel Synchornisation Improvements

`Bunny::Session#with_channel` is now fully synchronised and won't run into `COMMAND_INVALID` errors
when used from multiple threads that share a connection.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.

