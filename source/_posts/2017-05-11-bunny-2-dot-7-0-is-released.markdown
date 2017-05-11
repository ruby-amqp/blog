---
layout: post
title: "Bunny 2.7.0 is released"
date: 2017-05-11 15:17
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.7.0](https://rubygems.org/gems/bunny/versions/2.7.0) is released to rubygems.org.

`2.7.0` is a maintenance release that introduces a couple of minor
breaking changes.

In case your applications use Date/Time/DateTime serialisation with Bunny,
all of them must upgraded to `2.7.0` at the same time.



## Changes between Bunny 2.6.x and 2.7.0 (May 11th, 2017)

### amq-protocol Update

Minimum `amq-protocol` version is now [`2.2.0`]](https://github.com/ruby-amqp/amq-protocol/blob/master/ChangeLog.md#changes-between-210-and-220-may-11th-2017) which includes
a change in [how timestamps are encoded](https://github.com/ruby-amqp/amq-protocol/issues/64).


### `Bunny::ContinuationQueue#poll` Less Prone to Race Conditions

`Bunny::ContinuationQueue#poll` was reworked with feedback from Joseph Wong.

GitHub issue: [#462](https://github.com/ruby-amqp/bunny/issues/462)


### Recovery Attempt Counting Strategy Changed

Previous behehavior is not unreasonable but is not what many users and
even RabbitMQ team members come to expect. Therefore it can be
considered a bug.

Previously a reconnection counter was preserved between successful
recoveries. This made the integration test that uses server-sent
connection.close possible.

With this change, the counter is reset after successful reconnection
but there's an option to go back to the original behavior. We also do
a hell of a lot more logging.

GitHub issue: [#408](https://github.com/ruby-amqp/bunny/issues/408)


### Absolute Windows File Paths are No Longer treated as Inline Certs

Contributed by Jared Smartt.

GitHub issue: [#492](https://github.com/ruby-amqp/bunny/issues/492).


### Opening a Channel on an Intentionally Closed Connection Immediately Raises an Exception

Contributed by Alessandro Verlato.

GitHub issue: [#465](https://github.com/ruby-amqp/bunny/issues/465)


### Bunny::ConsumerWorkPool#shutdown Terminates Early When It's Safe to Do So

`Bunny::ConsumerWorkPool#shutdown(true)` waited for consumer shutdown
even if the pool wasn't active (there were no consumers on its
channel).

GitHub issue: [#438](https://github.com/ruby-amqp/bunny/issues/438).


### Retry on new Ruby 2.1+ variations of `EAGAIN`, `EWOULDBLOCK`

GitHub issue: [#456](https://github.com/ruby-amqp/bunny/issues/456)


### Do Not Modify Host Arrays

Bunny now can work with frozen host arrays.

GitHub issue: [#446](https://github.com/ruby-amqp/bunny/issues/446)




## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.7.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
