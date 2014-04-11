---
layout: post
title: "Bunny 1.2.1 is released"
date: 2014-04-11 16:22
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.2.1](https://rubygems.org/gems/bunny/versions/1.2.1) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.2.0 and 1.2.1

### Better Synchronization for Publisher Confirms

Publisher confirms implementation now synchronizes unconfirmed
set better.

Contributed by Nicolas Viennot.

### Channel Allocation After Recovery

Channel id allocator is no longer reset after recovery
if there are channels open. Makes it possible to open channels
on a recovered connection (in addition to the channels
it already had).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.2.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
