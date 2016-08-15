---
layout: post
title: "Bunny 2.5.1 is released"
date: 2016-08-15 08:43
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.5.1](https://rubygems.org/gems/bunny/versions/2.5.1) is released to rubygems.org.

`2.5.1` is a maintenance release.


## Changes between Bunny 2.5.0 and 2.5.1

### More Defensive Consumer Work Pool

`Bunny::ConsumerWorkPool#join` and `Bunny::ConsumerWorkPool#pause`
no longer fails with a `NoMethodError` on nil when executed
on a work pool that doesn't have active threads (consumers).

This change is largely cosmetic and won't affect the majority
of of projects in any way.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.5.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
