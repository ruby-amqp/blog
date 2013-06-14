---
layout: post
title: "Bunny 0.9.0.rc1 is released"
date: 2013-06-14 22:15
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.rc1](https://rubygems.org/gems/bunny/versions/0.9.0.rc1) is released to rubygems.org.

This release adds TLS support and a couple of minor improvements. Bunny 0.9 is now feature
complete and used widely enough for us to be confident about labelling this an RC.


## Changes between Bunny 0.9.0.pre13 and 0.9.0.rc1

### TLS Support

Bunny 0.9 finally supports TLS. There are 3 new options `Bunny.new` takes:

 * `:tls` which, when set to `true`, will set SSL context up and switch to TLS port (5671)
 * `:tls_cert` which is a string path to the client certificate (public key) in PEM format
 * `:tls_key` which is a string path to the client key (private key) in PEM format
 * `:tls_ca_certificates` which is an array of string paths to CA certificates in PEM format

An example:

``` ruby
conn = Bunny.new(:tls                   => true,
                 :tls_cert              => "examples/tls/client_cert.pem",
                 :tls_key               => "examples/tls/client_key.pem",
                 :tls_ca_certificates   => ["./examples/tls/cacert.pem"])
```


### Bunny::Queue#pop_waiting

`Bunny::Queue#pop_waiting` is a new function that mimics `Bunny::Queue#pop`
but will wait until a message is available. It uses a `:timeout` option and will
raise an exception if the timeout is hit:

``` ruby
# given 1 message in the queue,
# works exactly as Bunny::Queue#get
q.pop_waiting

# given no messages in the queue, will wait for up to 0.5 seconds
# for a message to become available. Raises an exception if the timeout
# is hit
q.pop_waiting(:timeout => 0.5)
```

This method only makes sense for collecting Request/Reply ("RPC") replies.


### Bunny::InvalidCommand is now Bunny::CommandInvalid

`Bunny::InvalidCommand` is now `Bunny::CommandInvalid` (follows
the exception class naming convention based on response status
name).

[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.




## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 final:

 * Fix any remaining important issues we get reports for
 * Make configuring low-level socket and SSL context

We will also make improvements to the [documentation guides](http://rubybunny.info).


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
