---
layout: post
title: "March Hare 2.9.0 is released"
date: 2015-04-04 23:12
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.9.0](https://rubygems.org/gems/march_hare/versions/2.9.0-java) is
released to rubygems.org.

This is primarily a bug fix release.


## Changes Between 2.8.0 and 2.9.0

### TLS Connection Fixes

TLS connections with an explicitly provided TLS version and PKCS12 certificate
no longer fail. In addition, related connection have changed to

 * `:tls` (version as a string: `TLSv1`, `TLSv1.1`, `TLSv1.2`)
 * `:tls_certificate_path`: PKCS12 certificate path as a string
 * `:tls_certificate_password`: PKCS12 certificate password as a string

To quickly generate a PKCS12 certificate as well as CA and server certificate/key pair,
see [tls-gen](https://github.com/michaelklishin/tls-gen/).


### URI Connections Fix

Host selector no longer breaks connections that use URIs.

GH issue: [#73](https://github.com/ruby-amqp/march_hare/issues/73).


### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.5.1`.



## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
