---
layout: post
title: "Bunny 1.5.0 is released"
date: 2014-10-09 18:03
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.5.0](https://rubygems.org/gems/bunny/versions/1.5.0) is released to rubygems.org.

This is a minor feature and bug fix release.


## Changes between Bunny 1.4.0 and 1.5.0

### Improved Uncaught Exception Handler

Uncaught exception handler now provides more information about the exception,
including its caller (one more stack trace line).

Contributed by Carl Hörberg (CloudAMQP).


### Convenience Method for Temporary (Server-named, Exclusive) Queue Declaration

`Bunny::Channel#temporary_queue` is a convenience method that declares a new
server-named exclusive queue:

``` ruby
q = ch.temporary_queue
```

Contributed by Daniel Schierbeck (Zendesk).

### Recovery Reliability Improvements

Automatic connection recovery robustness improvements.
Contributed by Andre Foeken (Nedap).

### Host Lists

It is now possible to pass the `:hosts` option to `Bunny.new`/`Bunny::Session#initialize`.
When connection to RabbitMQ (including during connection recovery), a random host
will be chosen from the list.

Connection shuffling and robustness improvements.

Contributed by Andre Foeken (Nedap).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/1.5.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
