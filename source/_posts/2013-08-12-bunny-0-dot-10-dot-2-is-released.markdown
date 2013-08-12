---
layout: post
title: "Bunny 0.10.2 is released"
date: 2013-08-12 09:06
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.10.2](https://rubygems.org/gems/bunny/versions/0.10.2) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.10.x`.

We encourage all Bunny users to upgrade to it.


## Changes between Bunny 0.10.1 and 0.10.2

### Consumers Can Be Re-Registered From Bunny::Consumer#handle_cancellation

It is now possible to re-register a consumer (and use any other synchronous methods)
from `Bunny::Consumer#handle_cancellation`, which is now invoked in the channel's
thread pool.


### Bunny::Session#close Fixed for Single Threaded Connections

`Bunny::Session#close` with single threaded connections no longer fails
with a nil pointer exception.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
