---
layout: post
title: "Bunny 2.3.0 is released"
date: 2016-02-28 11:24
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.3.0](https://rubygems.org/gems/bunny/versions/2.3.0) is released to rubygems.org.

`2.3.0` is a minor feature release.



## Changes between Bunny 2.2.0 and 2.3.0

### Thread#abort_on_exception Setting for Consumer Work Pool Threads

`Bunny::Session#create_channel` now supports a 3rd argument that,
when set to `true`, makes consumer work pool threads to have
`Thread#abort_on_exception` set on them.

GH issue: [#382](https://github.com/ruby-amqp/bunny/pull/382)

Contributed by Seamus Abshere.

### Explicit Transport Closure on Recovery

Bunny now will explicitly close previosly used transport before starting
connection recovery.

GitHub issue: [#377](https://github.com/ruby-amqp/bunny/pull/377).

Contributed by bkanhoopla.

### No TLS Socket Double-init

Makes sure that TLS sockets are not double-initialized.

GH issue: [#345](https://github.com/ruby-amqp/bunny/issues/345).

Contributed by Carl Hörberg.

### Lazily Evaluated Debug Log Strings

GH issue: [#375](https://github.com/ruby-amqp/bunny/pull/375)

Contributed by Omer Katz.




## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.

