---
layout: post
title: "Bunny 1.1.1 is released"
date: 2014-01-30 13:34
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.1](https://rubygems.org/gems/bunny/versions/1.1.1) is released to rubygems.org.

This is a usability release.


## Changes between Bunny 1.0.0 and 1.1.1

### Uncaught Consumer Exceptions

Uncaught consumer exceptions are now handled by uncaught exceptions
handler that can be defined per channel:

``` ruby
ch.on_uncaught_exception do |e, consumer|
  # ...
end
```

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
