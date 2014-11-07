---
layout: post
title: "Bunny 1.6.2 is released"
date: 2014-11-07 11:19
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.6.2](https://rubygems.org/gems/bunny/versions/1.6.2) is released to rubygems.org.

1.6.2 is a bug fix release.


## Changes between Bunny 1.6.1 and 1.6.2

### JRuby Writes Fixes

On JRuby, Bunny reverts back to using plain old `write(2)` for writes. The CRuby implementation
on JRuby suffers from I/O incompatibilities. Until JRuby

Bunny users who run on JRuby are highly recommended to switch to [March Hare](http://rubymarchhare.info),
which has nearly identical API and is significantly more efficient.



## Changes between Bunny 1.6.0 and 1.6.1

### Bunny::Session#with_channel Synchornisation Improvements

`Bunny::Session#with_channel` is now fully synchronised and won't run into `COMMAND_INVALID` errors
when used from multiple threads that share a connection.

## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
