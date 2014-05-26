---
layout: post
title: "Bunny 1.2.2 is released"
date: 2014-05-26 11:32
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.2.2](https://rubygems.org/gems/bunny/versions/1.2.2) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.2.1 and 1.2.2

### Synchronization Improvements for Session#close

`Bunny::Session#close` now better synchronizes state transitions,
eliminating a few race condition scenarios with I/O reader thread.

### Bunny::Exchange.default Fix

`Bunny::Exchange.default` no longer raises an exception.

Note that it is a legacy compatibility method. Please use
`Bunny::Channel#default_exchange` instead.

Contributed by Justin Litchfield.

GH issue [#211](https://github.com/ruby-amqp/bunny/pull/211).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.2.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
