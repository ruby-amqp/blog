---
layout: post
title: "Bunny 0.9.4 is released"
date: 2013-07-25 16:37
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.4](https://rubygems.org/gems/bunny/versions/0.9.4) is released to rubygems.org.

This is a usability improvement release that is **completely backwards compatible**
with `0.9.0`.

We encourage all Bunny users to upgrade to it.



## Changes between Bunny 0.9.3 and 0.9.4

### Client TLS Certificates are Optional

Bunny will no longer require client TLS certificates. Note that CA certificate
list is still necessary.

If RabbitMQ TLS configuration requires peer verification, client certificate
and private key are mandatory.



[Full change log](https://github.com/ruby-amqp/bunny/blob/0.9.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
