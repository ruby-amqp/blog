---
layout: post
title: "amqp gem 1.1.6 is Released"
date: 2013-12-10 12:12
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.1.5](https://rubygems.org/gems/amqp/versions/1.1.5) is released to rubygems.org.

This release is 100% backwards compatible.


## Changes Between 1.1.5 and 1.1.6

### 65535 Channels Per Connection

amqp gem now allows for 65535 channels per connection and
not Ruby process.

Contributed by [Neo](http://neo.com) developers.


## Changes Between 1.1.4 and 1.1.5

### channel.close is Delayed Until After Channel is Open

This eliminates a race condition in some codebases that use
very short lived channels.

Contributed by [Neo](http://neo.com) developers.


## Changes Between 1.1.3 and 1.1.4

### ConnectionClosedError is Back

`ConnectionClosedError` is now defined again.

Contributed by Carl Hörberg.


## Changes Between 1.1.2 and 1.1.3

### Fixed Exception in AMQP::Exchange#handle_declare_ok

`AMQP::Exchange#handle_declare_ok` no longer raises an exception
about undefined method.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
