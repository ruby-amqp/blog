---
layout: post
title: "Hutch 0.14.0 is Released"
date: 2015-02-23 23:16
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.14.0](https://rubygems.org/gems/hutch/versions/0.14.0) is released to rubygems.org.

This is a minor feature release.


## Changes Between 0.13.0 and 0.14.0

### Configurable Socket Timeouts

Socket read and write timeouts are now configurable using
the `read_timeout` and `write_timeout` options, respectively.

Contributed by Chris Barton.


### Logged Messages as Serialised as JSON

...as opposed to Ruby object printing.

Contributed by Andrew Morton.


### Configurable Heartbeat

Config now supports a new option: `:heartbeat`, which is passed
on to Bunny.

Contributed by Simon Taranto.


### HoneyBadger Error Handler

Contributed by Daniel Farrell.


### Hutch.connected? Now Returns Up-to-Date Value

`Hutch.connected?` no longer relies on an ivar and always returns
an up-to-date value.

Contributed by Pierre-Louis Gottfrois.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

