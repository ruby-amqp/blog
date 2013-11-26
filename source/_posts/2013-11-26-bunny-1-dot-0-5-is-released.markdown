---
layout: post
title: "Bunny 1.0.5 is released"
date: 2013-11-26 12:42
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.5](https://rubygems.org/gems/bunny/versions/1.0.5) is released to rubygems.org.

This is a bug fix release.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.4 and 1.0.5

### Single Threaded Mode Fixes

Single threaded mode no longer fails with

```
undefined method `event_loop'
```

### connection.tune.channel_max No Longer Overflows

`connection.tune.channel_max` could previously be configured to values
greater than 2^16 - 1 (65535). This would result in a silent overflow
during serialization. The issue was harmless in practice but is still
a bug that can be quite confusing.

Bunny now caps max number of channels to 65535. This allows it to be
forward compatible with future RabbitMQ versions that may allow limiting
total # of open channels via server configuration.

### Thread Leaks Fixes

Bunny will now correctly release heartbeat sender when allocating
a new one (usually happens only when connection recovers from a network
failure).

### amq-protocol Update

Minimum `amq-protocol` version is now `1.9.0` which includes
bug fixes and performance improvements for channel ID allocator.



[Full change log](https://github.com/ruby-amqp/bunny/blob/1.0.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
