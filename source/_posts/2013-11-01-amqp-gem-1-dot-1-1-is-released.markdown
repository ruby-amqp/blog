---
layout: post
title: "amqp gem 1.1.1 is Released"
date: 2013-11-01 22:08
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.1.1](https://rubygems.org/gems/amqp/versions/1.1.1) is released to rubygems.org.

This is a bug fix release that is 100% backwards compatible.


## Changes between amqp gem 1.1.0 and 1.1.1

### Fixed Exception in AMQP::Exchange#handle_declare_ok

`AMQP::Exchange#handle_declare_ok` no longer raises an exception
about undefined method `#anonymous?`.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
