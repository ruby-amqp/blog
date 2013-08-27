---
layout: post
title: "Bunny 0.10.5 is released"
date: 2013-08-28 01:33
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.10.5](https://rubygems.org/gems/bunny/versions/0.10.5) is released to rubygems.org.

This is a bug fix release that is **completely backwards compatible**
with `0.10.x`.

We encourage all Bunny users to upgrade to it.


## Changes between Bunny 0.10.4 and 0.10.5

### Ruby 1.8 Compatibility

Bunny is Ruby 1.8-compatible again and no longer references
`RUBY_ENGINE`.

### Bunny::Session.parse_uri

`Bunny::Session.parse_uri` is a new method that parses
connection URIs into hashes that `Bunny::Session#initialize`
accepts.

``` ruby
Bunny::Session.parse_uri("amqp://user:pwd@broker.eng.megacorp.local/myapp_qa")
```


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
