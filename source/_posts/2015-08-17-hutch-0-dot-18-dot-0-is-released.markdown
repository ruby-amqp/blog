---
layout: post
title: "Hutch 0.18.0 is Released"
date: 2015-08-17 10:30
comments: false
categories: 
  - hutch
  - releases
---

## TL;DR

[Hutch 0.18.0](https://rubygems.org/gems/hutch/versions/0.18.0) is released to rubygems.org.

This is a minor feature release.


## Changes Between 0.17.0 and 0.18.0

### JRuby Support (Using March Hare)

Hutch will now use March Hare when running on JRuby.
This will yield significant throughput and core utilisation
improvements for workloads with many and/or busy consumers.

Contributed by Teodor Pripoae.


### Configurable Consumer Thread Pool Size

`:consumer_pool_size` is a new option (defaults to `1`) which defines
Bunny consumer work pool size.

Contributed by Derek Kastner.

### Bunny Logger Option

`:client_logger` is a new option that allows
for configuring loggerd used by Bunny, the underlying
RabbitMQ client library.

Contributed by Nate Salisbury.


## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

