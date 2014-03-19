---
layout: post
title: "Bunny 1.1.5 is released"
date: 2014-03-19 11:17
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.5](https://rubygems.org/gems/bunny/versions/1.1.5) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.1.4 and 1.1.5

### Thread Leak Plugged

`Bunny::Session#close` on connections that have experienced a network failure
will correctly clean up I/O thread.


## Changes between Bunny 1.1.3 and 1.1.4

### Bunny::Concurrent::ContinuationQueue#poll Rounding Fix

`Bunny::Concurrent::ContinuationQueue#poll` no longer floors the argument
to the nearest second.

Contributed by Brian Abreu.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
