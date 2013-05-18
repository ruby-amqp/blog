---
layout: post
title: "Bunny 0.9.0.pre12 is released"
date: 2013-05-18 18:48
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre12](https://rubygems.org/gems/bunny/versions/0.9.0.pre12) is released to rubygems.org.

This release fixes a couple of regressions that affected publisher confirms
and Ruby 1.8 compatibility.


## Changes between Bunny 0.9.0.pre11 and 0.9.0.pre12

### Ruby 1.8 Compatibility Regression Fix

`Bunny::Socket` no longer uses Ruby 1.9-specific constants.


### Bunny::Channel#wait_for_confirms Return Value Regression Fix

`Bunny::Channel#wait_for_confirms` returns `true` or `false` again.



## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Fix any remaining important issues we get reports for
 * Finish TLS support



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
