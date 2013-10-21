---
layout: post
title: "March Hare 2.0.0.rc3 is Released"
date: 2013-10-21 23:42
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.0.0.rc3](https://rubygems.org/gems/march_hare/versions/2.0.0.rc3) is
released to rubygems.org.

This release is a release candidate of `2.0` that introduces another
usability improvement.

2.0 should be production ready from the stability perspective but has
**breaking API changes**.



## Changes Between 2.0.0-rc2 and 2.0.0-rc3

## Consumer Work Pool Tuning Improvements

MarchHare 1.x used to maintain a separate executor (thread pool) per non-blocking
consumer. This is not optimal and reimplements the wheel RabbitMQ Java client
already has invented: it dispatches consumer methods in a thread pool maintained
by every connection.

Instead of maintaining its own executor, MarchHare now relies on the Java client
to do the job. The **key difference** is that `1.x` versions used to maintain
a thread pool per channel while `2.x` has a thread pool **per connection**.

`rc3` introduces an easier way to configure the executor: it is now sufficient
to only provide pool size. For example:

``` ruby
MarchHare.connect(:thread_pool_size => 16)
```

It is still possible to override the executor when opening a connection by
providing an executor factory (any Ruby callable):

``` ruby
MarchHare.connect(:executor_factory => Proc.new {
  MarchHare::ThreadPools.fixed_of_size(16)
})
```

## Change Log

[Full change log for 2.0](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md#changes-between-150-and-200) is available on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
