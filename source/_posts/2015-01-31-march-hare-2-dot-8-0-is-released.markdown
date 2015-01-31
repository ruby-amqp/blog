---
layout: post
title: "March Hare 2.8.0 is released"
date: 2015-01-31 09:03
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.8.0](https://rubygems.org/gems/march_hare/versions/2.8.0-java) is
released to rubygems.org.

This is a minor feature release.


## Changes Between 2.7.0 and 2.8.0

### Support P12 Certificates for TLS Connections

It is now possible to use P12 certificates with the Bunny-like
connection options:

 * `:tls_key_cert` (a file path)
 * `:certificate_password` (as a Ruby string)

Contributed by Simon Yu.

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.4.3`.

### Host List Selection Improvements

Host selection from the list is now randomised.

Contributed by Michael Ries.

### Support for Consumer Callbacks with Arity < 0

Callbacks with arity < 0 now can be used delivery handlers.
See [Method#arity](http://www.ruby-doc.org/core-2.2.0/Method.html#method-i-arity)
documentation for more info.

Contributed by Roman Lishtaba.



## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
