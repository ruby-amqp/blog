---
layout: post
title: "Bunny 1.1.7 is released"
date: 2014-03-20 11:48
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.7](https://rubygems.org/gems/bunny/versions/1.1.7) is released to rubygems.org.

This is a bug fix release.

## Changes between Bunny 1.1.6 and 1.1.7

### Heartbeat Sender Thread Leak

`Bunny::Session#close` no longer leaks heartbeat sender
threads.

Contributed by m-o-e.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
