---
layout: post
title: "amq-protocol 1.9.0 is Released"
date: 2013-11-21 23:22
comments: false
categories:
  - amq-protocol
  - bunny
  - "amqp gem"
  - releases
---


amq-protocol `1.9.0` is released.

This is a maintenance release that [drastically improves
throughput](https://github.com/ruby-amqp/amq-protocol/pull/35) of the
channel id allocator, as well as correcting some bugs in it. If you
use Bunny or amqp gem, upgrading amq-protocol is highly recommended.


## Changes between 1.8.0 and 1.9.0

### Performance Improvements in AMQ::BitSet

`AMQ::BitSet#next_clear_bit` is now drastically more efficient
(down from 6 minutes for 10,000 iterations to 4 seconds for 65,536 iterations).

Contributed by Doug Rohrer, Dave Anderson, and Jason Voegele from
[Neo](http://www.neo.com).


[Full change log](https://github.com/ruby-amqp/amq-protocol/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
