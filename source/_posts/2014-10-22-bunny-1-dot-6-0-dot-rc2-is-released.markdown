---
layout: post
title: "Bunny 1.6.0.rc2 is released"
date: 2014-10-22 11:00
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.6.0.rc2](https://rubygems.org/gems/bunny/versions/1.6.0-rc2) is released to rubygems.org.

1.6 is a minor feature release that makes the library use TLS 1.0 or later
when possible.


## Changes between Bunny 1.5.0 and 1.6.0-rc2

### TLSv1 by Default

TLS connections now prefer TLSv1 (or later, if available) due to the recently discovered
[POODLE attack](https://www.openssl.org/~bodo/ssl-poodle.pdf) on SSLv3.

Contributed by Michael Klishin (Pivotal) and Justin Powers (Desk.com).

GH issues:

 * [#259](https://github.com/ruby-amqp/bunny/pull/259)
 * [#260](https://github.com/ruby-amqp/bunny/pull/260)
 * [#261](https://github.com/ruby-amqp/bunny/pull/261)


### Socket Read and Write Timeout Improvements

Bunny now sets a read timeout on the sockets it opens, and uses
`IO.select` timeouts as the most reliable option available
on Ruby 1.9 and later.

GH issue: [#254](https://github.com/ruby-amqp/bunny/pull/254).

Contributed by Andre Foeken (Nedap).

### Inline TLS Certificates Support

TLS certificate options now accept inline certificates as well as
file paths.

GH issues: [#255](https://github.com/ruby-amqp/bunny/pull/255), [#256](https://github.com/ruby-amqp/bunny/pull/256).

Contributed by Will Barrett (Sqwiggle).



## Full Change Log

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
