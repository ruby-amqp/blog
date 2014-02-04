---
layout: post
title: "March Hare 2.1.2 is released"
date: 2014-02-04 12:43
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.1.2](https://rubygems.org/gems/march_hare/versions/2.1.2) is
released to rubygems.org.

This is a bug fix release.


## Changes Between 2.1.1 and 2.1.2

### Internal Exchanges

Exchanges now can be declared as internal:

``` ruby
ch = conn.create_channel
x  = ch.fanout("marchhare.tests.exchanges.internal", :internal => true)
```

Internal exchanges cannot be published to by clients and are solely used
for [Exchange-to-Exchange bindings](http://rabbitmq.com/e2e.html) and various
plugins but apps may still need to bind them. Now it is possible
to do so with March Hare.


## Full Change Log

Please consult the [change
log](https://github.com/ruby-amqp/march_hare/blob/2.1.x-stable/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
