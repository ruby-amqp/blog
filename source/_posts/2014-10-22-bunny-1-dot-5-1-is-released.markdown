---
layout: post
title: "Bunny 1.5.1 is released"
date: 2014-10-22 12:18
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.5.1](https://rubygems.org/gems/bunny/versions/1.5.1) is released to rubygems.org.

This is a security release.


## Changes between Bunny 1.5.0 and 1.5.1

### TLSv1 by Default

TLS connections now prefer TLSv1 (or later, if available) due to the recently discovered
[POODLE attack](https://www.openssl.org/~bodo/ssl-poodle.pdf) on SSLv3.

Contributed by Michael Klishin (Pivotal) and Justin Powers (Desk.com).

GH issues:

 * [#259](https://github.com/ruby-amqp/bunny/pull/259)
 * [#260](https://github.com/ruby-amqp/bunny/pull/260)
 * [#261](https://github.com/ruby-amqp/bunny/pull/261)



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.5.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
