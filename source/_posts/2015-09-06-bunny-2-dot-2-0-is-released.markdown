---
layout: post
title: "Bunny 2.2.0 is released"
date: 2015-09-06 02:50
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 2.2.0](https://rubygems.org/gems/bunny/versions/2.2.0) is released to rubygems.org.

`2.2.0` is a minor feature release.


## Changes between Bunny 2.1.0 and 2.2.0

### Add :addresses to connect options

Before this the connection options only allowed multiple hosts, an
address is a combination of a host and a port. This makes it possible to
specify different hosts with different ports.

Contributed by Bart van Zon (Tele2).

### Recover from connection.close by default

Bunny will now try to reconnect also when server sent connection.close is
received, e.g. when a server is restarting (but also when the connection is
force closed by the server). This is in-line with how many other clients behave.
The old default was `recover_from_connection_close: false`.

Contributed by Carl Hörberg (CloudAMQP).


## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) maintains Bunny and several other RabbitMQ client libraries.

