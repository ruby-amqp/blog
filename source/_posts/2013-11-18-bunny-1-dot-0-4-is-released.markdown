---
layout: post
title: "Bunny 1.0.4 is released"
date: 2013-11-18 16:36
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.4](https://rubygems.org/gems/bunny/versions/1.0.4) is released to rubygems.org.

This is a bug fix release.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.3 and 1.0.4

### Versioned Delivery Tag Fix

Versioned delivery tag now ensures all the arguments it operates
(original delivery tag, atomic fixnum instances, etc) are coerced to `Integer`
before comparison.

GitHub issues: #171.


[Full change log](https://github.com/ruby-amqp/bunny/blob/1.0.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
