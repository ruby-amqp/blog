---
layout: post
title: "Bunny 0.9.0.rc2 is released"
date: 2013-06-27 14:01
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.rc2](https://rubygems.org/gems/bunny/versions/0.9.0.rc2) is released to rubygems.org.

This release fixes a couple of issues discovered since RC1. Bunny 0.9 is now feature
complete and used widely enough for us to be going through the RC stage.

If you use an earlier Bunny version, **please help us test 0.9 RCs**!


## Changes between Bunny 0.9.0.rc1 and 0.9.0.rc2

### Channel Now Properly Restarts Consumer Pool

In a case when all consumers are cancelled, `Bunny::Channel`
will shut down its consumer delivery thread pool.

It will also now mark the pool as not running so that it can be
started again successfully if new consumers are registered later.

GH issue: #133.


### Bunny::Queue#pop_waiting is Removed

A little bit of background: on MRI, the method raised `ThreadErrors`
reliably. On JRuby, we used a different [internal] queue implementation
from JDK so it wasn't an issue.

`Timeout.timeout` uses `Thread#kill` and `Thread#join`, both of which
eventually attempt to acquire a mutex used by Queue#pop, which Bunny
currently uses for continuations. The mutex is already has an owner
and so a ThreadError is raised.

This is not a problem on JRuby because there we don't use Ruby's
Timeout and Queue and instead rely on a JDK concurrency primitive
which provides "poll with a timeout".

[The issue with `Thread#kill` and `Thread#raise`](http://blog.headius.com/2008/02/ruby-threadraise-threadkill-timeoutrb.html)
has been first investigated and blogged about by Ruby implementers
in 2008.

Finding a workaround will probably take a bit of time and may involve
reimplementing standard library and core classes.

We don't want this issue to block Bunny 0.9 release. Neither we want
to ship a broken feature.  So as a result, we will drop
Bunny::Queue#pop_waiting since it cannot be reliably implemented in a
reasonable amount of time on MRI.

Per issue #131.


### More Flexible SSLContext Configuration

Bunny will now upgrade connection to SSL in `Bunny::Session#start`,
so it is possible to fine tune SSLContext and socket settings
before that:

``` ruby
require "bunny"

conn = Bunny.new(:tls                   => true,
                 :tls_cert              => "examples/tls/client_cert.pem",
                 :tls_key               => "examples/tls/client_key.pem",
                 :tls_ca_certificates   => ["./examples/tls/cacert.pem"])

puts conn.transport.socket.inspect
puts conn.transport.tls_context.inspect
```

This also means that `Bunny.new` will now open the socket. Previously
it was only done when `Bunny::Session#start` was invoked.



[Full change log](https://github.com/ruby-amqp/bunny/blob/master/ChangeLog.md) can be found on GitHub.




## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 final:

 * Fix any remaining important issues we get reports for
 * Make configuring low-level socket and SSL context

We will also make improvements to the [documentation guides](http://rubybunny.info).


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
