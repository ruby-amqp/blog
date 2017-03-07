---
layout: post
title: "Bunny 2.6.4 is released"
date: 2017-03-07 13:30
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.6.4](https://rubygems.org/gems/bunny/versions/2.6.4) is released to rubygems.org.

`2.6.4` is a maintenance release.


## Changes between Bunny 2.6.3 and 2.6.4

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

### Opening a Channel on an Intentionally Closed Connection Immediately Raises an Exception

Contributed by Alessandro Verlato.

GitHub issue: [#465](https://github.com/ruby-amqp/bunny/issues/465)


## Changes between Bunny 2.6.2 and 2.6.3

### Retry on new Ruby 2.1+ variations of `EAGAIN`, `EWOULDBLOCK`

GitHub issue: [#456](https://github.com/ruby-amqp/bunny/issues/456)



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.6.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
