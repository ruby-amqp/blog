---
layout: post
title: "Bunny 1.0.0.rc1 is released"
date: 2013-10-02 00:08
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.0.rc1](https://rubygems.org/gems/bunny/versions/1.0.0.rc1) is released to rubygems.org.

This is a release candidate for `1.0`, a major milestone for Bunny. It is 100% backwards
compatible with `0.10.x`.


## Changes between Bunny 1.0.0.pre6 and 1.0.0.rc1

### amq-protocol Update

Minimum `amq-protocol` version is now `1.8.0` which includes
a bug fix for messages exactly 128 Kb in size.


### Add timeout Bunny::ConsumerWorkPool#join

`Bunny::ConsumerWorkPool#join` now accepts an optional
timeout argument.


## Plans for 1.0.0 Final

We plan to release Bunny `1.0.0` on October 29th, 2013. The library
has had its soaking period in the last few months and several issues
were fixed during `0.10.x` releases.

It has being adopted by many commercial users and fairly mature open source projects, such as [Hutch](http://rabbitmq.1065348.n5.nabble.com/Hutch-Inter-service-communication-with-Ruby-and-RabbitMQ-td29471.html).

Now is a good time to give Bunny a try, help us improve the [documentation](http://rubybunny.info)
and report any usability issues you may find.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
