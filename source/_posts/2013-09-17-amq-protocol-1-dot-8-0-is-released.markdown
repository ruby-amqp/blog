---
layout: post
title: "amq-protocol 1.8.0 is released"
date: 2013-09-17 08:37
comments: false
categories:
  - releases
  - bunny
  - "amqp gem"
  - amq-protocol
---

amq-protocol `1.8.0` is released.

This is a bug fix release. If you use Bunny or amqp gem, upgrading amq-protocol
is highly recommended.


## Changes between 1.7.0 and 1.8.0

### Body Framing Fix

Messages exactly 128 Kb in size had one extra (empty) body
frame.


Contributed by Nicolas Viennot.




[Full change log](https://github.com/ruby-amqp/amq-protocol/blob/master/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
