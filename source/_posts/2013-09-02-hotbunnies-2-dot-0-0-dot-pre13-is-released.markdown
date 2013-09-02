---
layout: post
title: "HotBunnies 2.0.0.pre13 is released"
date: 2013-09-02 18:35
comments: false
categories:
  - hot_bunnies
  - jruby
  - releases
---

## TL;DR

[HotBunnies
2.0.0.pre13](https://rubygems.org/gems/hot_bunnies/versions/2.0.0.pre13)
is released to rubygems.org.

This release is a development milestone. `2.0.0.pre13` focuses on improving
network connection recovery.

2.0 should be production ready from the stability perspective but has **breaking API changes**.
Please consult the change log below before considering upgrading.


## Changes Between 2.0.0.pre12 and 2.0.0.pre13

### Continuous Reconnection

HotBunnies will now continuously try to reconnect after network failure (every N seconds
at the moment, no exponential backoff).


## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Add logging
 * Review API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
