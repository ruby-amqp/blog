---
layout: post
title: "Bunny 2.3.1 is released"
date: 2016-04-06 22:55
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.3.1](https://rubygems.org/gems/bunny/versions/2.3.1) is released to rubygems.org.

`2.3.1` is a maintenance release.


## Changes between Bunny 2.3.0 and 2.3.1

### Support (Quoted) IPv6 Addresses in Address Lists

GitHub issue: [#383](https://github.com/ruby-amqp/bunny/issues/383).

Contributed by Jeremy Heiler.

### Transport#read_fully Doesn't Try to Recover

Since transport is replaced by a recovering connection
anyway, and this produces confusing errors up the stack.

GitHub issue: [#359](https://github.com/ruby-amqp/bunny/issues/359)

Contributed by Donal McBreen.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
