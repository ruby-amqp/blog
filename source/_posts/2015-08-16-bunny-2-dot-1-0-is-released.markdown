---
layout: post
title: "Bunny 2.1.0 is released"
date: 2015-08-16 17:05
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.1.0](https://rubygems.org/gems/bunny/versions/2.1.0) is released to rubygems.org.

`2.1.0` is a bug fix release that introduces a breaking change.


### Changes between Bunny 2.0.0 and 2.1.0

Bunny 2.1.0 has an **important breaking change**. It is highly
advised that 2.1.0 is not mixed with earlier versions of Bunny
in case your applications include **integers in message headers**.

### Integer Value Serialisation in Headers

Integer values in headers are now serialised as signed 64-bit integers. Previously
they were serialised as 32-bit unsigned integers, causing both underflows
and overflows: incorrect values were observed by consumers.

It is highly
advised that 2.1.0 is not mixed with earlier versions of Bunny
in case your applications include integers in message headers.

If that's not the case, Bunny 2.1 will integeroperate with any earlier version
starting with 0.9.0 just fine. Popular clients in other languages
(e.g. Java and .NET) will interoperate with Bunny 2.1.0 without
issues.


### Explicit Ruby 2.0 Requirement

Bunny now requires Ruby 2.0 in the gemspec.

Contributed by Carl Hörberg.

### JRuby Fix

Bunny runs again on JRuby. Note that
JRuby users are strongly advised to use March Hare instead.

Contributed by Teodor Pripoae.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.

