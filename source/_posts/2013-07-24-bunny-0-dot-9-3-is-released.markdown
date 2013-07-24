---
layout: post
title: "Bunny 0.9.3 is released"
date: 2013-07-24 16:11
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.3](https://rubygems.org/gems/bunny/versions/0.9.3) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.9.0`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.2 and 0.9.3

### Publishing Over Closed Connections

Publishing a message over a closed connection (during a network outage, before the connection
is open) will now correctly result in an exception.

Contributed by Matt Campbell.



[Full change log](https://github.com/ruby-amqp/bunny/blob/0.9.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
