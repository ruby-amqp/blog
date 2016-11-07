---
layout: post
title: "March Hare 2.20.0 is released"
date: 2016-11-07 16:27
comments: false
categories:
  - march_jare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.20.0](https://rubygems.org/gems/march_hare/versions/2.20.0-java) is
released to rubygems.org.

This is a maintenance release.


## Changes Between 2.19.0 and 2.20.0 (November 2nd, 2016)

### Connection Recovery Should Retry on Protocol Handshake Timeout

When an intermediary such as HAproxy with no backends online
(or a problematic server node) doesn't respond to a protocol header sent
to it, RabbitMQ Java client will throw a generic operation timeout exception
because the heartbeat mechanism is not yet enabled (it has not yet negotiated
a timeout value for it!)

March Hare should handle this exception and retry, as if it was an I/O or skipped heartbeats
exception.

Kudos to Andrew Cholakian and Jordan Sissel for digging this issue out.

GitHub issues: [#107](https://github.com/ruby-amqp/march_hare/issues/107),
               [logstash-plugins/logstash-input-rabbitmq#76](https://github.com/logstash-plugins/logstash-input-rabbitmq/issues/76#issuecomment-257722124)



## Changes Between 2.18.0 and 2.19.0 (October 26th, 2016)

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to a milestone version of `3.6.6`
to include a number of bug fixes early.


### Thread Pool Leak

GitHub issue: [#97](https://github.com/ruby-amqp/march_hare/issues/97).

Contributed by Michael Reis.


### Removed Unused Thread Pool

March Hare relies on RabbitMQ Java client for consumer dispatch
but one (unused) thread pool was still instantiated.

GitHub issue: [#96](https://github.com/ruby-amqp/march_hare/issues/96).

Contributed by Ivo Anjo.


### Channel Allocation Failure Throws an Exception

GitHub issue: [#98](https://github.com/ruby-amqp/march_hare/issues/98).

Contributed by Michael Reis.



## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
