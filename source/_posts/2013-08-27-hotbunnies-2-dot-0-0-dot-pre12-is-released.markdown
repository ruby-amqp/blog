---
layout: post
title: "HotBunnies 2.0.0.pre12 is released"
date: 2013-08-27 14:28
comments: false
categories:
  - hot_bunnies
  - jruby
  - releases
---

## TL;DR

[HotBunnies
2.0.0.pre11](https://rubygems.org/gems/hot_bunnies/versions/2.0.0.pre11)
is released to rubygems.org.

This release is a development milestone. 2.0 focuses on usability and introduces a couple of
major API improvements and features.

2.0 should be production ready from the stability perspective but has **breaking API changes**.
Please consult the change log below before considering upgrading.


## Changes Between 2.0.0.pre11 and 2.0.0.pre12

### Make HotBunnies::Queue#subscribe Respect All Options

Make `HotBunnies::Queue#subscribe` respect all options it used to accept
before `pre11` again.


## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Further test automatic network failure recovery
 * Make TLS support more configurable, ideally with the same API as Bunny 0.10
 * Add logging
 * Review API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
