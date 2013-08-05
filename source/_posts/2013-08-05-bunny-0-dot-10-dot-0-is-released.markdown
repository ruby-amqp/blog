---
layout: post
title: "Bunny 0.10.0 is released"
date: 2013-08-05 12:44
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.10.0](https://rubygems.org/gems/bunny/versions/0.10.0) is released to rubygems.org.

This is a usability improvement release that is **one breaking API change**
with `0.9.x`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.8 and 0.10.0

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

This involves an API change: `Bunny::DeliveryMetadata#delivery_tag` is now
and instance of a class that responds to `#tag` and `#to_i` and is accepted
by `Bunny::Channel#ack` and related methods.

Integers are still accepted by the same methods.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
