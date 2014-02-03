---
layout: post
title: "amqp gem 1.3.0 is Released"
date: 2014-02-03 13:39
comments: false
categories:
  - "amgp gem"
  - releases
---

## TL;DR

[amqp gem 1.3.0](https://rubygems.org/gems/amqp/versions/1.3.0) is released to rubygems.org.

This release includes a couple of minor features.


## Changes Between 1.2.0 and 1.3.0

### Exchange-to-Exchange Bindings Support

amqp gem now supports [Exchange-to-Exchange Bindings](http://www.rabbitmq.com/e2e.html), a RabbitMQ
extension.

`AMQP::Exchange#bind` and `AMQP::Exchange#unbind` work very much like `AMQP::Queue#bind` and
`AMQP::Queue#unbind`, with the argument exchange being the source one.

Contributed by Stefan Kaes.

### Internal Exchange Declaration

amqp gem now supports declaration of internal exchanges
(used via exchange-to-exchange bindings, cannot be published to
by clients).

To declare an exchange as internal, add `:internal => true` to
declaration options.

Contributed by Stefan Kaes.


### Initial Connection Failures Retries

Set connection status to closed on connection failure, which
means connection retries succeed.

Contributed by Marius Hanne.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/amqp/blob/1.2.x-stable/ChangeLog.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
