---
layout: post
title: "March Hare 2.5.0 is released"
date: 2014-07-18 01:40
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.5.0](https://rubygems.org/gems/march_hare/versions/2.5.0) is
released to rubygems.org.

This is primarily a bug fix release.


## Changes Between 2.4.0 and 2.5.0

### Bugfixes

* Consumers are now properly unregistered from their owning channel during recovery (#52)
* Sessions in recovery are no longer reported active until recovery has fully completed (#55)
* Error 320 (connection-forced) is now properly handled (#53)
* Fixed a race condition that could cause subscriptions utilizing manual acks to fail immediately after recovery (#54)

Contributed by Chris Heald.



## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
