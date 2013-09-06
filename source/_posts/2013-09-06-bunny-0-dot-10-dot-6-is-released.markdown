---
layout: post
title: "Bunny 0.10.6 is released"
date: 2013-09-06 10:04
comments: false
categories: 
---

## TL;DR

[Bunny 0.10.6](https://rubygems.org/gems/bunny/versions/0.10.6) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.10.x`. We encourage all Bunny users to upgrade to it.


## Changes between Bunny 0.10.5 and 0.10.6

### Respect RABBITMQ_URL value

`RABBITMQ_URL` env variable will now have effect even if
Bunny.new is invoked without arguments.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
