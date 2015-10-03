---
layout: post
title: "March Hare 2.13.0 is released"
date: 2015-10-03 09:09
comments: false
categories:
  - jruby
  - march_hare
  - releases
---

## TL;DR

[March Hare 2.13.0](https://rubygems.org/gems/march_hare/versions/2.13.0-java) is
released to rubygems.org.

This is a maintenance release.


## Changes Between 2.12.0 and 2.13.0

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.5.5`.



## Changes Between 2.11.0 and 2.12.0

### Ruby Exceptions Thrown by More Public Methods

 * `Channel#exchange_declare`
 * `Channel#exchange_bind`
 * `Channel#exchange_unbind`

now raise Ruby exceptions instead of their Java counterparts.

Contributed by Thilo-Alexander Ginkel.

### Connection Recovery Fixed For Connections Using URIs

Connection recovery no longer fails silently if the `:uri` option was used in `Connection#new`.

Contributed by Noah Magram. 


## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
