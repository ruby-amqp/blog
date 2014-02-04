---
layout: post
title: "Bunny 1.1.2 is released"
date: 2014-02-04 12:43
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.2](https://rubygems.org/gems/bunny/versions/1.1.2) is released to rubygems.org.

This is a usability release.


## Changes between Bunny 1.1.1 and 1.1.2

### Internal Exchanges

Exchanges now can be declared as internal:

``` ruby
ch = conn.create_channel
x  = ch.fanout("bunny.tests.exchanges.internal", :internal => true)
```

Internal exchanges cannot be published to by clients and are solely used
for [Exchange-to-Exchange bindings](http://rabbitmq.com/e2e.html) and various
plugins but apps may still need to bind them. Now it is possible
to do so with Bunny.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
