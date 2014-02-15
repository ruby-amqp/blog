---
layout: post
title: "Bunny 1.1.3 is released"
date: 2014-02-15 12:47
comments: false
categories: 
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.3](https://rubygems.org/gems/bunny/versions/1.1.3) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.1.2 and 1.1.3

### Nagle's Algorithm Disabled Correctly

Bunny now properly disables [Nagle's algorithm](http://boundary.com/blog/2012/05/02/know-a-delay-nagles-algorithm-and-you/)
on the sockets it opens. This likely means
significantly lower latency for workloads that involve
sending a lot of small messages very frequently:

![](https://f.cloud.github.com/assets/1800798/2175168/ac09c4dc-95ba-11e3-93d9-a28fb25a8327.png)

[Contributed](https://github.com/ruby-amqp/bunny/pull/187) by Nelson Gauthier (AirBnB).


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
