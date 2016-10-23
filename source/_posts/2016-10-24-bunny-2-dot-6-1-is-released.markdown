---
layout: post
title: "Bunny 2.6.1 is released"
date: 2016-10-24 02:24
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.6.1](https://rubygems.org/gems/bunny/versions/2.6.1) is released to rubygems.org.

`2.6.1` is a maintenance release.



## Changes between Bunny 2.6.0 and 2.6.1

### Bunny::ConsumerWorkPool#shutdown Terminates Early When It's Safe to Do So

`Bunny::ConsumerWorkPool#shutdown(true)` waited for consumer shutdown
even if the pool wasn't active (there were no consumers on its
channel).

GitHub issue: [#438](https://github.com/ruby-amqp/bunny/issues/438).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.6.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
