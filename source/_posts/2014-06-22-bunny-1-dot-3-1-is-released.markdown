---
layout: post
title: "Bunny 1.3.1 is released"
date: 2014-06-22 14:06
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.3.1](https://rubygems.org/gems/bunny/versions/1.3.1) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.3.0 and 1.3.1

### NoMethodError on Thread During Shutdown

During abnormal termination, `Bunny::Session#close` no longer tries
to call the non-existent `terminate_with` method on its origin
thread.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.3.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
