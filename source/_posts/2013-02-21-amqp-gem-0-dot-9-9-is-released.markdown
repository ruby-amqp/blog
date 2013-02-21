---
layout: post
title: "amqp gem 0.9.9 is released"
date: 2013-02-21 21:08
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 0.9.9](https://rubygems.org/gems/amqp/versions/0.9.9) is released to rubygems.org.

This release includes a few bug fixes and minor improvements. It is 100% backwards
compatible.


## Change Log

  * Large [> 128K] messages with non-ASCII characters are now framed  correctly (as of amq-protocol 1.2.0).
  * Minor efficiency improvements in basic.publish serialization code.
  * Heartbeats delivery is now paused when a network failure is detected.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
