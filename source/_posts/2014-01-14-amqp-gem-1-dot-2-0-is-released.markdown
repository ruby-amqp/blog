---
layout: post
title: "amqp gem 1.2.0 is Released"
date: 2014-01-14 14:45
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.2.0](https://rubygems.org/gems/amqp/versions/1.2.0) is released to rubygems.org.

This release is 100% backwards compatible.


## Changes Between 1.1.0 and 1.2.0

### [Authentication Failure Notification](http://www.rabbitmq.com/auth-notification.html) Support

amqp gem now supports [Authentication Failure
Notification](http://www.rabbitmq.com/auth-notification.html). Public
API for authentication failure handling hasn't changed.

This extension is available in RabbitMQ 3.2+.

## basic.qos Recovery Fix

`basic.qos` setting will now be recovered first thing after
channel recovery, to the most recent value passed via `:prefetch` channel
constructor option or `AMQP::Channel#prefetch`.


### amq-protocol Update

Minimum `amq-protocol` version is now `1.9.2`.

### Automatic Recovery Fix

Automatic connection recovery now correctly recovers bindings again.

Contributed by Devin Christensen.


### 65535 Channels Per Connection

amqp gem now allows for	65535 channels per connection and
not Ruby process.

Contributed by Neo (http://neo.com) developers.

### channel.close is Delayed Until After Channel is Open

This eliminates a race condition in some codebases that use
very short lived channels.

### ConnectionClosedError is Back

`ConnectionClosedError` from `amq-client` is now defined again.


### Fixed Exceptions in AMQP::Exchange#handle_declare_ok

`AMQP::Exchange#handle_declare_ok` no longer raises an exception
about undefined methods `#anonymous?` and `#exchange`.


[Full change log](https://github.com/ruby-amqp/amqp/blob/1.2.x-stable/ChangeLog.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
