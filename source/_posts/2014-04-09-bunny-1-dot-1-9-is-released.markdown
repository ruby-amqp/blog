---
layout: post
title: "Bunny 1.1.9 is released"
date: 2014-04-09 13:56
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.9](https://rubygems.org/gems/bunny/versions/1.1.9) is released to rubygems.org.

This is a bug fix release and the last release in `1.1.x` series.


## Changes between Bunny 1.1.8 and 1.1.9

### :key Supported in Bunny::Channel#queue_bind

It is now possible to use `:key` (which Bunny versions prior to 0.9 used)
as well as `:routing_key` as an	 argument to `Bunny::Queue#bind`.

### System Exceptions Not Rescued by the Library

Bunny now rescues `StandardError` instead of `Exception` where
it automatically does so (e.g. when dispatching deliveries to consumers).

Contributed by Alex Young.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
