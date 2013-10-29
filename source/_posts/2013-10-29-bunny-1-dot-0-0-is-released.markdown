---
layout: post
title: "Bunny 1.0.0 is released"
date: 2013-10-29 17:34
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.0](https://rubygems.org/gems/bunny/versions/1.0.0) is released to rubygems.org.

This is the `1.0.0` GA release, a major milestone for Bunny. It is
100% backwards compatible with `0.10.x`.


## Finally 1.0.0

[Bunny](http://rubybunny.info) is not a new library. Started in early
2009 by Chris Duncan, it was full of limitations for a few
years. However, it also was the easiest Ruby client to use and did not
have some inherent limitations of [amqp gem](http://rubyamqp.info).

In 2012 and 2013, Bunny pretty much rewritten from scratch for the
0.9.0 release to address the limitation, as well as redesign it for
the multicore CPUs age.  In addition, [documentation
guides](http://rubybunny.info) were ported from amqp gem.  Dozens
refinement releases and a few RCs later, it is in a good shape to go
1.0.

Since 0.9.0 shipped, Bunn has being adopted by many commercial users
and fairly mature open source projects, such as
[Hutch](http://rabbitmq.1065348.n5.nabble.com/Hutch-Inter-service-communication-with-Ruby-and-RabbitMQ-td29471.html).

If you are new to Bunny, take a look at the
[documentation](http://rubybunny.info).  Then join
[rabbitmq-discuss](https://lists.rabbitmq.com/cgi-bin/mailman/listinfo/rabbitmq-discuss)
and [Ruby RabbitMQ clients mailing
list](https://groups.google.com/group/ruby-amqp).

We hope you will enjoy using Bunny!


## Changes between Bunny 1.0.0.rc2 and 1.0.0

### [Authentication Failure Notification](http://www.rabbitmq.com/auth-notification.html) Support

`Bunny::AuthenticationFailureError` is a new auth failure exception
that subclasses `Bunny::PossibleAuthenticationFailureError` for
backwards compatibility.

As such, `Bunny::PossibleAuthenticationFailureError`'s error message
has changed.

This extension is available in RabbitMQ 3.2+.


### Bunny::Session#exchange_exists?

`Bunny::Session#exchange_exists?` is a new predicate that makes it
easier to check if a exchange exists.

It uses a one-off channel and `exchange.declare` with `passive` set to true
under the hood.

### Bunny::Session#queue_exists?

`Bunny::Session#queue_exists?` is a new predicate that makes it
easier to check if a queue exists.

It uses a one-off channel and `queue.declare` with `passive` set to true
under the hood.


### Inline TLS Certificates and Keys

It is now possible to provide inline client
certificate and private key (as strings) instead
of filesystem paths. The options are the same:

 * `:tls` which, when set to `true`, will set SSL context up and switch to TLS port (5671)
 * `:tls_cert` which now can be a client certificate (public key) in PEM format
 * `:tls_key` which now can be a client key (private key) in PEM format
 * `:tls_ca_certificates` which is an array of string paths to CA certificates in PEM format

For example:

``` ruby
conn = Bunny.new(:tls                   => true,
                 :tls_cert              => ENV["TLS_CERTIFICATE"],
                 :tls_key               => ENV["TLS_PRIVATE_KEY"],
                 :tls_ca_certificates   => ["./examples/tls/cacert.pem"])
```



## Changes between Bunny 1.0.0.rc1 and 1.0.0.rc2

### Ruby 1.8.7 Compatibility Fixes

Ruby 1.8.7 compatibility fixes around timeouts.


## Changes between Bunny 1.0.0.pre6 and 1.0.0.rc1

### amq-protocol Update

Minimum `amq-protocol` version is now `1.8.0` which includes
a bug fix for messages exactly 128 Kb in size.


### Add timeout Bunny::ConsumerWorkPool#join

`Bunny::ConsumerWorkPool#join` now accepts an optional
timeout argument.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
