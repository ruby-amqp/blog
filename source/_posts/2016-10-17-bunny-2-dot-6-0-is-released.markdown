---
layout: post
title: "Bunny 2.6.0 is released"
date: 2016-10-17 00:54
comments: false
categories: 
  - bunny
  - releases
---

## TL;DR

[Bunny 2.6.0](https://rubygems.org/gems/bunny/versions/2.6.0) is released to rubygems.org.

`2.6.0` is a maintenance release.



## Changes between Bunny 2.5.0 and 2.6.0

### Graceful Shutdown of Consumers

Consumer work pool will now allow for a grace period before stopping
pool threads so that delivery processing in progress can have a chance to finish.

GitHub issue: [#437](https://github.com/ruby-amqp/bunny/pull/437)

Contributed by Stefan Sedich.

### `Bunny::Channel#wait_for_confirms` Now Throws When Used on a Closed Channel

GitHub issue: [#428](https://github.com/ruby-amqp/bunny/pull/428)

Contributed by Dimitar Dimitrov.

### Race Condition Eliminated in `Bunny::Channel#wait_for_confirms`

GitHub issue: [#424](https://github.com/ruby-amqp/bunny/issues/424)

Contributed by Dimitar Dimitrov.

### More Defensive Consumer Work Pool

`Bunny::ConsumerWorkPool#join` and `Bunny::ConsumerWorkPool#pause`
no longer fails with a `NoMethodError` on nil when executed
on a work pool that doesn't have active threads (consumers).

This change is largely cosmetic and won't affect the majority
of of projects in any way.




## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.6.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
