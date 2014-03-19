---
layout: post
title: "Bunny 1.1.6 is released"
date: 2014-03-19 19:05
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.6](https://rubygems.org/gems/bunny/versions/1.1.6) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.1.5 and 1.1.6

### Cherry-picked Missing Commit from Master

`Bunny::Session#clean_up_on_shutdown` was cherry-picked from master.

### Routing Key Limit

Per AMQP 0-9-1 spec, routing keys cannot be longer than 255 characters.
`Bunny::Channel#basic_publish` and `Bunny::Exchange#publish` now enforces
this limit.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
