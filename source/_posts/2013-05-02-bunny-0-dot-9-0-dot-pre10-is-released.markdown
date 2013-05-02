---
layout: post
title: "Bunny 0.9.0.pre10 is released"
date: 2013-05-02 11:29
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre10](https://rubygems.org/gems/bunny/versions/0.9.0.pre10) is released to rubygems.org.

This is a bug fix release. It **includes one breaking API change**


## Changes between Bunny 0.9.0.pre9 and 0.9.0.pre10

This release contains a **breaking API change**.

### Concurrency Improvements On JRuby

On JRuby, Bunny now will use `java.util.concurrent`-backed implementations
of some of the concurrency primitives. This both improves client stability
(JDK concurrency primitives has been around for 9 years and have
well-defined, documented semantics) and opens the door to solving
some tricky failure handling problems in the future.


### Explicitly Closed Sockets

Bunny now will correctly close the socket previous connection had
when recovering from network issues.


### Bunny::Exception Now Extends StandardError

`Bunny::Exception` now inherits from `StandardError` and not `Exception`.

Naked rescue like this

``` ruby
begin
  # ...
rescue => e
  # ...
end
```

catches only descendents of `StandardError`. Most people don't
know this and this is a very counter-intuitive practice, but
apparently there is code out there that can't be changed that
depends on this behavior.

This is a **breaking API change**.




## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Add logging
 * Finish TLS support
 * Make network failure recovery even more flexible



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
