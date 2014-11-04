---
layout: post
title: "March Hare 2.7 is released"
date: 2014-11-04 14:29
comments: false
categories:
  - march_hare
  - releases
---

## TL;DR

[March Hare 2.7.0](https://rubygems.org/gems/march_hare/versions/2.7.0) is
released to rubygems.org.

This is a minor feature release.


## Changes Between 2.6.0 and 2.7.0

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.4.1`.

### Host List Selection Improvements

Host selection from the list is now randomised.

Contributed by Michael Ries.



## Changes Between 2.5.0 and 2.6.0

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.4.0`.

### Host Lists

It is now possible to pass the `:hosts` option to `MarchHare.connect`. When
connection to RabbitMQ (including during connection recovery), a random host
will be chosen from the list.

### Better Bunny Compatibility: the Heartbeat Option

`MarchHare.connect` now accepts `:heartbeat` as an alias for `:heartbeat_requested`
for better Bunny compatibility (and because API reference accidentally listed it).

GH issue: #57.


## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
