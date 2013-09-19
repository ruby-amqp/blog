---
layout: post
title: "amqp gem 1.1.0-rc1 is released"
date: 2013-09-19 18:51
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.1.0.rc1](https://rubygems.org/gems/amqp/versions/1.1.0.rc1) is released to rubygems.org.

This release is ready for amqp gem users to try it out. It includes
a couple of usability improvements, internal code reorganization (`amq-client`
is no longer used), `amq-protocol` update and more long time deprecated
API elements removed.

All users are encouraged to try this new version to make upgrading to
`1.1.0` easy in the future.



## Changes Between 1.0.0 and 1.1.0

### amq-protocol Update

Minimum `amq-protocol` version is now `1.8.0` which includes
a bug fix for messages exactly 128 Kb in size.


### AMQ::Client is Removed

`amq-client` has been incorporated into amqp gem. `AMQ::Client` and related
modules are no longer available.

### AMQP::Channel#confirm_select is Now Delayed

`AMQP::Channel#confirm_select` is now delayed until after the channel
is opened, making it possible to use it with the pseudo-synchronous
code style.

### RabbitMQ Extensions are Now in Core

amqp gem has been targeting RabbitMQ exclusively for a while now.

RabbitMQ extensions are now loaded by default and will be even more
tightly integrated in the future.

### AMQP::Channel.default is Removed

`AMQP::Channel.default` and method_missing-based operations on the default
channel has been removed. They've been deprecated since 0.6.

### AMQP::Channel#rpc is Removed

`AMQP::RPC`-related code has been removed. It has been deprecated
since 0.7.

### AMQP::Channel.on_error is Removed

Long time deprecated `AMQP::Channel.on_error` is removed.



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
