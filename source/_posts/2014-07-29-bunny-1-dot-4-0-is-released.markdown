---
layout: post
title: "Bunny 1.4.0 is released"
date: 2014-07-29 10:16
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.4.0](https://rubygems.org/gems/bunny/versions/1.4.0) is released to rubygems.org.

This is a usability and bug fix release.


## Changes between Bunny 1.3.x and 1.4.0

### Channel#wait_for_confirms Returns Immediately If All Publishes Confirmed

Contributed by Matt Campbell.

### Publisher Confirms is In Sync After Recovery

When a connection is recovered, the sequence counter resets on the
broker, but not the client. To keep things in sync the client must store a confirmation
offset after a recovery.

Contributed by Devin Christensen.

### NoMethodError on Thread During Shutdown

During abnormal termination, `Bunny::Session#close` no longer tries
to call the non-existent `terminate_with` method on its origin
thread.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.4.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
