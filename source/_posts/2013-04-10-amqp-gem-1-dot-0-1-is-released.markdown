---
layout: post
title: "amqp gem 1.0.1 is released"
date: 2013-04-10 20:27
comments: false
categories: 
  - releases
  - "amqp gem"
---

## TL;DR

[amqp gem 1.0.1](https://rubygems.org/gems/amqp/versions/1.0.1) is released to rubygems.org.

This release has bug fixes by upgrading `amq-protocol` dependency to `1.3.0+`.


## Changes between amqp gem 1.0.0 and 1.0.1

### amq-protocol Bug Fixes

 * `amq-protocol` now correctly serializes floats (both 32 and 64 bits) in attribute tables.
 * Byte values (8 bit signed integers) deserialization is now supported.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
