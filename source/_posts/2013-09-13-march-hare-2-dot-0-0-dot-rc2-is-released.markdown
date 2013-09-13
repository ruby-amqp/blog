---
layout: post
title: "March Hare 2.0.0.rc2 is released"
date: 2013-09-13 19:57
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.0.0.rc2](https://rubygems.org/gems/march_hare/versions/2.0.0.rc2) is
released to rubygems.org.

This release is a release candidate of `2.0` that introduces one
usability improvement.

2.0 should be production ready from the stability perspective but has
**breaking API changes**.  Please consult the change log below before
considering upgrading.



## Changes Between 2.0.0-rc1 and 2.0.0-rc2

### Idempotent MarchHare::Consumer#cancel

`MarchHare::Consumer#cancel` is now idempotent.



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
