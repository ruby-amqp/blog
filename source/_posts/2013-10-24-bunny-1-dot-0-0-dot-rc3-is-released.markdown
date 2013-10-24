---
layout: post
title: "Bunny 1.0.0.rc3 is released"
date: 2013-10-24 08:40
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 1.0.0.rc3](https://rubygems.org/gems/bunny/versions/1.0.0.rc3) is released to rubygems.org.

This is a minor feature and usability release.
We encourage all Bunny users to upgrade to it.


## Changes between Bunny 1.0.0.rc2 and 1.0.0.rc3

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



[Full change
log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can
be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
