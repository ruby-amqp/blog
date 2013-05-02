---
layout: post
title: "amqp gem 1.0.2 is released"
date: 2013-05-02 10:01
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.0.2](https://rubygems.org/gems/amqp/versions/1.0.2) is released to rubygems.org.

This release has bug fixes.


## Changes between amqp gem 1.0.0 and 1.0.2

### AMQP::Channel#reuse Fixes

Channels that `AMQP::Channel#reuse` was called on now properly execute
all channel lifecycle callbacks again.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
