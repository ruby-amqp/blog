---
layout: post
title: "March Hare 2.0.0.rc5 is released"
date: 2013-11-16 23:09
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.0.0.rc5](https://rubygems.org/gems/march_hare/versions/2.0.0.rc5) is
released to rubygems.org.

This release is a release candidate of `2.0` that focuses on
usability improvements and bug fixes in automatic connection recovery.

2.0 should be production ready from the stability perspective but has
**breaking API changes**.  Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md) to learn
about the changes.



## Changes Between 2.0.0-rc4 and 2.0.0-rc5

### Connection Recovery Improvements

Automatic connection recovery has seen a few bug fixes,
most notably channel recovery failures no longer terminate
recovery of other channels on the same connection.

Channel recovery is now also performed in ascendant order of channel
ID's, which typically corresponds to the order in which channels
were opened.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
