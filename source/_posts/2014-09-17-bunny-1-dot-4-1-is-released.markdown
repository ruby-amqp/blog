---
layout: post
title: "Bunny 1.4.1 is released"
date: 2014-09-17 12:20
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.4.1](https://rubygems.org/gems/bunny/versions/1.4.1) is released to rubygems.org.

This is a bug fix release.


## Changes between Bunny 1.4.0 and 1.4.1

### Prevent Default Channel From Being Re-opened Twice on Recovery

Bunny's default channel (a relic from the `0.7.x` days when channels were not
even part of the API) is no longer recovered one time too many.

Contributed by Carl Chatfield.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.4.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
