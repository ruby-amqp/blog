---
layout: post
title: "Bunny 0.10.1 is released"
date: 2013-08-07 08:51
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.10.1](https://rubygems.org/gems/bunny/versions/0.10.1) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.10.x`.

We encourage all Bunny users to upgrade to it.


## Changes between Bunny 0.10.0 and 0.10.1

### Fixes for Abnormally Slow Bunny::Connection#close on JRuby

`Bunny::Connection#close` on JRuby sometimes could enter a waiting
state [on a native NIO/kqueue method] that lasted up to over 10 seconds.

This severely affected test suite run times.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
