---
layout: post
title: "Bunny 1.0.6 is released"
date: 2013-12-11 16:17
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.6](https://rubygems.org/gems/bunny/versions/1.0.6) is released to rubygems.org.

This is a bug fix release.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.5 and 1.0.6

### Better Exception Handling in Consumers

Consumer work pools will now correctly catch all exceptions
when dispatching submitted operations, not just `Bunny::Exception`
subclasses.

### TLS Without Peer Verification

Bunny now successfully performs TLS upgrade when peer verification
is disabled.

Contribute by Jordan Curzon.

### Bunny::Session#with_channel Ensures the Channel is Closed

`Bunny::Session#with_channel` now makes sure the channel is closed
even if provided block raises an exception

Contributed by Carl Hoerberg.


### Channel Number = 0 is Rejected

`Bunny::Session#create_channel` will now reject channel number 0.



[Full change log](https://github.com/ruby-amqp/bunny/blob/1.0.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
