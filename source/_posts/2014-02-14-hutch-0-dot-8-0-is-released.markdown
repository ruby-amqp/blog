---
layout: post
title: "Hutch 0.8.0 is Released"
date: 2014-02-14 09:45
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.8.0](https://rubygems.org/gems/hutch/versions/0.8.0) is released to rubygems.org.

This release introduces several minor new features.


## Changes Between 0.7.0 and 0.8.0

### Uncaught Exceptions Result in Rejected Messages

Uncaught exceptions in consumers now result in Hutch rejecting
messages (deliveries) using `basic.nack`. This way they are [dead lettered](http://www.rabbitmq.com/dlx.html).

Contributed by Garrett Johnson.

### Missing Require

`hutch/consumer.rb` no longer fails to load with the
apps that do not `require "set"`.

Contributed by Garrett Johnson.

### Relaxed Queue Namespace Validation

Namespaces now can include any characters that are valid in RabbitMQ
queue names.

Contributed by Garrett Johnson.

### basic.qos Configuration

It is now possible to configure `basic.qos` (aka channel prefetch) setting
used by Hutch using the `:channel_prefetch` config key.

### Passwords No Longer Logged

Hutch now elides passwords from logs.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

