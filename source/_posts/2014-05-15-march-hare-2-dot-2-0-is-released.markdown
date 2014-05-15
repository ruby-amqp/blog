---
layout: post
title: "March Hare 2.2.0 is released"
date: 2014-05-15 12:34
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.2.0](https://rubygems.org/gems/march_hare/versions/2.2.0) is
released to rubygems.org.

This is a bug fix release.


## Changes Between 2.1.x and 2.2.0

### IOExceptions Conversion Fix

Causeless IOExceptions and SocketExceptions thrown by the Java client are
correctly converted to `IOError` in Ruby land.

### Client-side Flow Control Removed

`MarchHare::Channel#channel_flow` is removed. Client-side flow control
has been deprecated for some time and is now removed in the Java client.

### Confirm Hooks Recovery

Confirm hooks (callbacks) are now recovered automatically.

Contributed by Noah Magram.

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.3.x`.

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


### Custom Executor Shutdown

`MarchHare::Session#close` now will always shut down the custom
executor service it was using, if any.

### Ruby 1.8 Support Dropped

March Hare no longer officially supports Ruby 1.8.



## Full Change Log

Please consult the [change
log](https://github.com/ruby-amqp/march_hare/blob/2.2.x-stable/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
