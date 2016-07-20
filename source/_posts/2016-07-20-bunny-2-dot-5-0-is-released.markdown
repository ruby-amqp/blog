---
layout: post
title: "Bunny 2.5.0 is released"
date: 2016-07-20 15:10
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.5.0](https://rubygems.org/gems/bunny/versions/2.5.0) is released to rubygems.org.

`2.5.0` is a maintenance release.


## Changes between Bunny 2.4.0 and 2.5.0

### Exchange Bindings are Now Correctly Recovered

GitHub issue: [#410](https://github.com/ruby-amqp/bunny/issues/410)

Contributed by Andrew Bruce.


### `Bunny::Channel#wait_for_confirms` Awaits While There're Outstanding Unconfirmed Messages

GitHub issue: [#424](https://github.com/ruby-amqp/bunny/issues/424)

Contributed by Dimitar Dimitrov.


### Queue Recovery Respects the `:no_declare` Option

Queue recovery now respects the `:no_declare` option.


### `Bunny::Channel#wait_for_confirms` Throws Early

`Bunny::Channel#wait_for_confirms` now throws an exception
early when invoked on a closed channel.

GitHub issue: [#428](https://github.com/ruby-amqp/bunny/pull/428).

Contributed by Dimitar Dimitrov.



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/2.5.x-stable/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.
