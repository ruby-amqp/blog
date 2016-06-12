---
layout: post
title: "Bunny 2.4.0 is released"
date: 2016-06-12 18:59
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.4.0](https://rubygems.org/gems/bunny/versions/2.4.0) is released to rubygems.org.

`2.4.0` is a minor feature release.


## Changes between Bunny 2.3.0 and 2.4.0

### Unconfirmed Delivery Tag Set Reset on Network Recovery

Channels will now reset their unconfirmed delivery tag set after
recovery.

GitHub issue: [#406](https://github.com/ruby-amqp/bunny/pull/406)

Contributed by Bill Ruddock.

### Support (Quoted) IPv6 Addresses in Address Lists

GitHub issue: [#383](https://github.com/ruby-amqp/bunny/issues/383).

Contributed by Jeremy Heiler.

### Transport#read_fully Doesn't Try to Recover

Since transport is replaced by a recovering connection
anyway, and this produces confusing errors up the stack.

GitHub issue: [#359](https://github.com/ruby-amqp/bunny/issues/359)

Contributed by Donal McBreen.

### Client-Provided Session `:properties` Merged with Defaults

Client-Provided Session `:properties` will now be merged with defaults
instead of replacing them. This makes it much more convenient to
override a single key.

### More Predictable RABBITMQ_URL Handling

`RABBITMQ_URL` no longer will be used if any other
connection options are provided. This makes it possible
to use `RABBITMQ_URL` for some connections and options
for others in a single OS process.

GitHub issue: [#403](https://github.com/ruby-amqp/bunny/pull/403)

Contributed by Jimmy Petersen.


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.4.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
