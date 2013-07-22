---
layout: post
title: "Bunny 0.9.2 is released"
date: 2013-07-22 07:40
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.2](https://rubygems.org/gems/bunny/versions/0.9.2) is released to rubygems.org.

This is a stability improvement release that is **completely backwards compatible**
with `0.9.0`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.1 and 0.9.2

### Reliability Improvement in Automatic Network Failure Recovery

Bunny now ensures a new connection transport (socket) is initialized
before any recovery is attempted.


## Changes between Bunny 0.9.0 and 0.9.1

### Reliability Improvement in Bunny::Session#create_channel

`Bunny::Session#create_channel` now uses two separate mutexes to avoid
a (very rare) issue when the previous implementation would try to
re-acquire the same mutex and fail (Ruby mutexes are non-reentrant).


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.9.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
