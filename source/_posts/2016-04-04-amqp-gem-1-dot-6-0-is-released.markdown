---
layout: post
title: "amqp gem 1.6.0 is released"
date: 2016-04-04 08:36
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.6.0](https://rubygems.org/gems/amqp/versions/1.6.0) is released to rubygems.org.

This is a maintenance release that has no new features but updates
`amq-protocol` dependency and drops Ruby 1.9 support.


## Changes Between 1.5.0 and 1.6.0

### amq-protocol Update

Minimum `amq-protocol` version is now `2.0.1`.

### Provide More Details in TCP Connection Failure Exception

Contributed by Neil Hooey.

GH issue: [#222](https://github.com/ruby-amqp/amqp/issues/222).


### Ensures frameset is cleared after an unhandled exception

Ensures frameset is cleared after an unhandled exception.
This avoids confusing exceptions such as

```
undefined method `method_class' for #<AMQ::Protocol::BodyFrame:0x0000001e8a60b0>
```

Contributed by Michael Lutsiuk.

GH issue: [#218](https://github.com/ruby-amqp/amqp/issues/218)




## Full Change Log

[Full change log](https://github.com/ruby-amqp/amqp/blob/1.6.x-stable/ChangeLog.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
