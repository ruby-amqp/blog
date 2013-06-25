---
layout: post
title: "amqp gem 1.1.0.pre1 is released"
date: 2013-06-25 13:55
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.0.2](https://rubygems.org/gems/amqp/versions/1.0.2) is released to rubygems.org.

This release includes one bug fix, removes more long time deprecated code and makes
RabbitMQ extensions being part of the core (so they are always available, no need to load them separately).



## Changes Between 1.0.0 and 1.1.0

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
