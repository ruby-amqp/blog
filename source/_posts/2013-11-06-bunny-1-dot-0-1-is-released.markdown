---
layout: post
title: "Bunny 1.0.1 is released"
date: 2013-11-06 22:15
comments: false
categories:
  - bunny
  - releases
  - jruby
---

## TL;DR

[Bunny 1.0.1](https://rubygems.org/gems/bunny/versions/1.0.1) is released to rubygems.org.

This is a JRuby-specific bug fix release.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.0 and 1.0.1

### Default CA's Paths Are Disabled on JRuby

Bunny uses OpenSSL provided CA certificate paths. This
caused problems on some platforms on JRuby (see [jruby/jruby#155](https://github.com/jruby/jruby/issues/1055)).

To avoid these issues, Bunny no longer uses default CA certificate paths on JRuby
(there are no changes for other Rubies), so it's necessary to provide
CA certificate explicitly.

### Fixes CPU Burn on JRuby

Bunny now uses slightly different ways of continuously reading from the socket
on CRuby and JRuby, to prevent abnormally high CPU usage on JRuby after a
certain period of time (the frequency of `EWOULDBLOCK` being raised spiked
sharply).

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.0.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
