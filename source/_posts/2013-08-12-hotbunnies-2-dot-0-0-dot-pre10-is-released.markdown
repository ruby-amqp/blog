---
layout: post
title: "HotBunnies 2.0.0.pre10 is released"
date: 2013-08-12 09:06
comments: false
categories: 
  - releases
  - jruby
  - hot_bunnies
---

## TL;DR

[HotBunnies 2.0.0.pre10](https://rubygems.org/gems/hot_bunnies/versions/2.0.0.pre10) is released to rubygems.org.

This release is a development milestone. 2.0 focuses on usability and introduces a couple of
major API improvements and features.

2.0 should be production ready from the stability perspective but has **breaking API changes**.
Please consult the change log below before considering upgrading.


# Changes Between 2.0.0.pre8 and 2.0.0.pre10

## Automatic Connection Recovery

HotBunnies now supports automatic connection recovery from a network outage,
similar to the version [in Bunny](http://rubybunny.info/articles/error_handling.html).

It recovers

 * Connections
 * Shutdown hooks
 * Channels
 * Exchanges, queues and bindings declared on the connection
 * Consumers

and can be disabled by setting `:automatically_recover` connection option to `false`.

This is the first version that works correctly in many common cases, but we don't
consider it to be 100% ready to recommend yet.


## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Further test and improve automatic network failure recovery
 * Make TLS support more configurable, ideally with the same API as Bunny 0.9
 * Add logging
 * API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
