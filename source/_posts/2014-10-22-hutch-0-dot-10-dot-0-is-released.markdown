---
layout: post
title: "Hutch 0.10.0 is Released"
date: 2014-10-22 17:54
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.10.0](https://rubygems.org/gems/hutch/versions/0.10.0) is released to rubygems.org.

This release introduces several minor new features.


## 0.10.0 — Oct 22, 2014

### Configuration via URI

Hutch now supports a new configuration key, `:uri`, which allows
connection configuration via a URI.

Note that since the URI has to include credentials, this option
is not available on the command line.

### Bunny Update

Bunny is updated to `1.5.1`, which mitigates the POODLE attack
by disabling SSL 3.0 where possible.

### Payload in Error Handlers

Error handlers will now have access to message payload.

Contributed by Daniel Farrell.

### Exceptions in Error Handlers Don't Prevent Nacks

Exceptions in error handlers no longer prevent messages from being
`basic.nack`-ed.

### Pid File Support

`:pidfile` is a new configuration option that stores Hutch process
PID in a file at provided path.

Contributed by Rustam Sharshenov.

### More Info on Message

Bunny's `delivery_info`, `properties` and payload are now accessible on `Hutch::Message`.

Contributed by gregory.


### Optional Config Parameters

`Hutch::Config` constructor now accepts an extra hash of optional
configuration parameters.

Contributed by Ignazio Mostallino.


## 0.9.0 — May 13, 2014

### Platform-aware Signal Registration

Hutch will no longer attempt to register signal traps
for signals not supported by the environment (e.g. on by certain OSes).

Contributed by Tobias Matthies.

### TLS Fixes

Hutch now properly passes client TLS key and certificate to
Bunny.

Contributed by Eric Nelson.

### Bunny Update

Bunny is updated to 1.2.x which should offer
[much better latency](https://github.com/ruby-amqp/bunny/pull/187) for
workloads with lots of small messages published frequently.

### More Unit Testing Friendly CLI/Runner

`Hutch::CLI#run` now accepts a parameter and is easier to use
in automated tests.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

