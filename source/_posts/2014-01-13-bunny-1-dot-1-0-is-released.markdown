---
layout: post
title: "Bunny 1.1.0 is released"
date: 2014-01-13 14:21
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.1.0](https://rubygems.org/gems/bunny/versions/1.1.0) is released to rubygems.org.

This is a usability release that adds a few minor features to what's in `1.0.x`.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.0 and 1.1.0

### Synchronized Session#create_channel and Session#close_channel

Full bodies of `Bunny::Session#create_channel` and `Bunny::Session#close_channel`
are now synchronized, which makes sure concurrent `channel.open` and subsequent
operations (e.g. `exchange.declare`) do not result in connection-level exceptions
(incorrect connection state transitions).

### Corrected Recovery Log Message

Bunny will now use actual recovery interval in the log.

Contributed by Chad Fowler.


### Full Channel State Recovery

Channel recovery now involves recovery of publisher confirms and
transaction modes.


### TLS	Without Peer Verification

Bunny now successfully performs	TLS upgrade when peer verification
is disabled.

Contributed by Jordan Curzon.

### Bunny::Session#with_channel Ensures the Channel is Closed

`Bunny::Session#with_channel` now makes sure the channel is closed
even if provided block raises an exception

Contributed by Carl Hoerberg.



### Channel Number = 0 is Rejected

`Bunny::Session#create_channel` will now reject channel number 0.


### Single Threaded Mode Fixes

Single threaded mode no longer fails with

```
undefined method `event_loop'
```


### connection.tune.channel_max No Longer Overflows

`connection.tune.channel_max` could previously be configured to values
greater than 2^16 - 1 (65535). This would result in a silent overflow
during serialization. The issue was harmless in practice but is still
a bug that can be quite confusing.

Bunny now caps max number of channels to 65535. This allows it to be
forward compatible with future RabbitMQ versions that may allow limiting
total # of open channels via server configuration.

### amq-protocol Update

Minimum `amq-protocol` version is now `1.9.0` which includes
bug fixes and performance improvements for channel ID allocator.

### Thread Leaks Fixes

Bunny will now correctly release heartbeat sender when allocating
a new one (usually happens only when connection recovers from a network
failure).


### Versioned Delivery Tag Fix

Versioned delivery tag now ensures all the arguments it operates
(original delivery tag, atomic fixnum instances, etc) are coerced to `Integer`
before comparison.

GitHub issues: #171.

### User-Provided Loggers

Bunny now can use any logger that provides the same API as Ruby standard library's `Logger`:

``` ruby
require "logger"
require "stringio"

io = StringIO.new
# will log to `io`
Bunny.new(:logger => Logger.new(io))
```

### Default CA's Paths Are Disabled on JRuby

Bunny uses OpenSSL provided CA certificate paths. This
caused problems on some platforms on JRuby (see [jruby/jruby#155](https://github.com/jruby/jruby/issues/1055)).

To avoid these issues, Bunny no longer uses default CA certificate paths on JRuby
(there are no changes for other Rubies), so it's necessary to provide
CA certificate explicitly.

### Fixes CPU Burn on JRuby

Bunny now uses slightly different ways of continuously reading from the socket
on CRuby and JRuby, to prevent abnormally high CPU usage on JRuby after a
certain period of time (the frequency of `EWOULDBLOCK` being raised spiked
sharply).



[Full change log](https://github.com/ruby-amqp/bunny/blob/1.1.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
