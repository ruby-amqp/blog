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

### exchange.unbind Support

`HotBunnies::Exchange#unbind` is now provided to compliment
`HotBunnies::Exchange#bind`.

### Safe[r] basic.ack, basic.nack and basic.reject implementation

Previously if a channel was recovered (reopened) by automatic connection
recovery before a message was acknowledged or rejected, it would cause
any operation on the channel that uses delivery tags to fail and
cause the channel to be closed.

To avoid this issue, every channel keeps a counter of how many times
it has been reopened and marks delivery tags with them. Using a stale
tag to ack or reject a message will produce no method sent to RabbitMQ.
Note that unacknowledged messages will be requeued by RabbitMQ when connection
goes down anyway.

This involves an API change: `HotBunnies::Headers#delivery_tag` is now
and instance of a class that responds to `#to_i` and is accepted
by `HotBunnies::Channel#ack` and related methods.

Integers are still accepted by the same methods.



## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Further test automatic network failure recovery
 * Make TLS support more configurable, ideally with the same API as Bunny 0.10
 * Add logging
 * Review API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
