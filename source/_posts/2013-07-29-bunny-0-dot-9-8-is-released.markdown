---
layout: post
title: "Bunny 0.9.8 is released"
date: 2013-07-29 11:34
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.8](https://rubygems.org/gems/bunny/versions/0.9.8) is released to rubygems.org.

This is a usability improvement release that is **completely backwards compatible**
with `0.9.0`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.7 and 0.9.8

### Exclusivity Violation for Consumers Now Raises a Reasonable Exception

When a second consumer is registered for the same queue on different channels,
a reasonable exception (`Bunny::AccessRefused`) will be raised.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.9.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
