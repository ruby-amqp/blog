---
layout: post
title: "March Hare 2.1.1 is released"
date: 2014-01-30 13:34
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.1.1](https://rubygems.org/gems/march_hare/versions/2.1.1) is
released to rubygems.org.

This is a bug fix release.


## Changes Between 2.1.0 and 2.1.1

### Custom Executor Shutdown

`MarchHare::Session#close` now will always shut down the custom
executor service it was using, if any.


## Full Change Log

Please consult the [change
log](https://github.com/ruby-amqp/march_hare/blob/2.1.x-stable/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
