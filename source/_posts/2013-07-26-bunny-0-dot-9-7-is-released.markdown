---
layout: post
title: "Bunny 0.9.7 is released"
date: 2013-07-26 13:21
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.7](https://rubygems.org/gems/bunny/versions/0.9.7) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.9.0`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.6 and 0.9.7

### Reentrant Mutex Implementation

Bunny now allows mutex impl to be configurable, uses reentrant Monitor
by default.

Non-reentrant mutexes is a major PITA and may affect code that
uses Bunny.

Avg. publishing throughput with Monitor drops slightly from
5.73 Khz to 5.49 Khz (about 4% decrease), which is reasonable
for Bunny.

Apps that need these 4% can configure what mutex implementation
is used on per-connection basis.


## Changes between Bunny 0.9.5 and 0.9.6

### Eliminated Race Condition in Bunny::Session#close

`Bunny::Session#close` had a race condition that caused (non-deterministic)
exceptions when connection transport was closed before connection
reader loop was guaranteed to have stopped.


## Changes between Bunny 0.9.4 and 0.9.5

### connection.close Raises Exceptions on Connection Thread

Connection-level exceptions (including when a connection is closed via
management UI or `rabbitmqctl`) will now be raised on the connection
thread so they

 * can be handled by applications
 * do not start connection recovery, which may be uncalled for




[Full change log](https://github.com/ruby-amqp/bunny/blob/0.9.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
