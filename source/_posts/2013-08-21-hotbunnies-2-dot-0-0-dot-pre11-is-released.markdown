---
layout: post
title: "HotBunnies 2.0.0.pre11 is released"
date: 2013-08-21 00:58
comments: false
categories:
  - releases
  - jruby
  - hot_bunnies
---

## TL;DR

[HotBunnies
2.0.0.pre11](https://rubygems.org/gems/hot_bunnies/versions/2.0.0.pre11)
is released to rubygems.org.

This release is a development milestone. 2.0 focuses on usability and introduces a couple of
major API improvements and features.

2.0 should be production ready from the stability perspective but has **breaking API changes**.
Please consult the change log below before considering upgrading.


## Changes Between 2.0.0.pre10 and 2.0.0.pre11

### Consumer Work Pool Changes

HotBunnies 1.x used to maintain a separate executor (thread pool) per non-blocking
consumer. This is not optimal and reimplements the wheel RabbitMQ Java client
already has invented: it dispatches consumer methods in a thread pool maintained
by every connection.

Instead of maintaining its own executor, HotBunnies now relies on the Java client
to do the job.

It is still possible to override the executor when opening a connection by
providing an executor factory (any Ruby callable):

``` ruby
HotBunnies.connect(:executor_factory => Proc.new {
  HotBunnies::ThreadPools.fixed_of_size(16)
})
```

It has to be a factory to make sure we can allocate a new pool upon connection
recovery, since JVM executors cannot be cloned or restarted.

By default HotBunnies will rely on the default RabbitMQ Java client's
executor service, which has a fixed size of 5 threads.


## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Further test automatic network failure recovery
 * Make TLS support more configurable, ideally with the same API as Bunny 0.10
 * Add logging
 * API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
