---
layout: post
title: "March Hare 2.0.0 is released"
date: 2013-12-05 13:51
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.0.0](https://rubygems.org/gems/march_hare/versions/2.0.0) is
released to rubygems.org.

This release is the final release of `2.0`.

2.0 should be production ready from the stability perspective but has
**breaking API changes**. Please consult the [change
log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.



## Changes Between 1.5.0 and 2.0.0

March Hare (previously Hot Bunnies) 2.0 has **breaking API changes**.

### New Name

March Hare is the new project name. The previous name had a sexist
meaning (unintentionally) and changing it was long overdue.


### exchange.unbind Support

`MarchHare::Exchange#unbind` is now provided to compliment
`MarchHare::Exchange#bind`.

### Safe[r] basic.ack, basic.nack and basic.reject implementation

Previously if a channel was recovered (reopened) by automatic connection
recovery before a message was acknowledged or rejected, it would cause
any operation on the channel that uses delivery tags to fail and
cause the channel to be closed.

To avoid this issue, every channel keeps a counter of how many times
it has been reopened and marks delivery tags with them. Using a stale
tag to ack or reject a message will produce no method sent to RabbitMQ.
Note that unacknowledged messages will be requeued by RabbitMQ when connection
goes down anyway.

This involves an API change: `MarchHare::Headers#delivery_tag` is now
and instance of a class that responds to `#to_i` and is accepted
by `MarchHare::Channel#ack` and related methods.

Integers are still accepted by the same methods.

## Consumer Work Pool Changes

MarchHare 1.x used to maintain a separate executor (thread pool) per non-blocking
consumer. This is not optimal and reimplements the wheel RabbitMQ Java client
already has invented: it dispatches consumer methods in a thread pool maintained
by every connection.

Instead of maintaining its own executor, MarchHare now relies on the Java client
to do the job. The **key difference** is that `1.x` versions used to maintain
a thread pool per channel while `2.x` has a thread pool **per connection**.

It is still possible to override the executor when opening a connection by
providing an executor factory (any Ruby callable):

``` ruby
MarchHare.connect(:executor_factory => Proc.new {
  MarchHare::ThreadPools.fixed_of_size(16)
})
```

There is a shortcut that accepts a thread pool size
and takes care of the rest:

``` ruby
MarchHare.connect(:thread_pool_size => 16)
```

It has to be a factory to make sure we can allocate a new pool upon connection
recovery, since JVM executors cannot be cloned or restarted.

By default MarchHare will rely on the default RabbitMQ Java client's
executor service, which has a fixed size of 5 threads.


## Automatic Connection Recovery

MarchHare now supports automatic connection recovery from a network outage,
similar to the version [in Bunny](http://rubybunny.info/articles/error_handling.html).

It recovers

 * Connections
 * Shutdown hooks
 * Channels
 * Exchanges, queues and bindings declared on the connection
 * Consumers

and can be disabled by setting `:automatically_recover` connection option to `false`.



## Shutdown Callbacks

`MarchHare::Session#on_shutdown` and `MarchHare::Channel#on_shutdown` are two
new methods that register **shutdown hooks**. Those are executed when

 * Network connectivity to RabbitMQ is lost
 * RabbitMQ shuts down the connection (because of an error or management UI action)

The callbacks take two arguments: the entity that's being shutdown
(`MarchHare::Session` or `MarchHare::Channel`) and shutdown reason (an exception):

``` ruby
conn = MarchHare.connect
conn.on_shutdown |conn, reason|
  # ...
end
```

In addition, MarchHare channels will make sure consumers are gracefully
shutdown (thread pools stopped, blocking consumers unblocked).

These are initial steps towards easier to use error handling and recovery,
similar to what amqp gem and Bunny 0.9+ provide.


## MarchHare::Channel#on_confirm

`MarchHare::Channel#on_confirm` provides a way to define [publisher
confirms](http://www.rabbitmq.com/confirms.html) callbacks. Note that
it's typically more convenient to use
`MarchHare::Channel#wait_for_confirms` to wait for all outdated
confirms.


## connection.blocked, connection.unblocked Support

`MarchHare::Session#on_blocked` and `MarchHare::Session#on_unblocked`
are new methods that provide a way to define [blocked connection
notifications](http://www.rabbitmq.com/connection-blocked.html)
callbacks:

``` ruby
connection.on_blocked do |reason|
  puts "I am blocked now. Reason: #{reason}"
end

connection.on_unblocked do
  puts "I am unblocked now."
end
```


## Authentication Failure Notifications Support

MarchHare now supports [authentication failure notifications](http://www.rabbitmq.com/auth-notification.html) (new in RabbitMQ 3.2).


## MarchHare::Session#start

`MarchHare::Session#start` is a new no-op method that improves API
compatibility with [Bunny 0.9](http://rubybunny.info).

## MarchHare::Queue#subscribe_with, MarchHare::Queue#build_consumer

`MarchHare::Queue#subscribe_with` and `MarchHare::Queue#build_consumer` are new method
that allow using consumer objects, for example, to first instantiate a blocking consumer
and pass the reference around so it can be cancelled from a different thread later.

``` ruby
consumer_object  = q.build_consumer(:blocking => false) do |metadata, payload|
  # ...
end
consumer         = q.subscribe_with(consumer_object, :blocking => false)
```


## Consumer Cancellation Support

Passing a block for the `:on_cancellation` option to `MarchHare::Queue#subscribe`
lets you support [RabbitMQ consumer cancellation](http://www.rabbitmq.com/consumer-cancel.html). The block should take 3
arguments: a channel, a consumer and a consumer tag.


## MarchHare Operations Now Raise Ruby Exceptions

MarchHare used to expose RabbitMQ Java client's channel implementation
directly to Ruby code. This means that whenever an exception was raised,
it was a Java exception (commonly `java.io.IOException`, wrapping a shutdown
signal).

Not only this severely violates the Principle of Least Surprise, it also
makes it much harder to inspect the exception and figure out how to get
relevant information from it without reading the RabbitMQ Java client
source.

Hot Bunnies 2.0+ provides a Ruby implementation of `MarchHare::Channel`
which rescues Java exceptions and turns them into Ruby
exceptions.

For example, handling a `queue.bind` failure now can be demonstrated
with the following straightforward test:

``` ruby
context "when the exchange does not exist" do
  it "raises an exception" do
    ch = connection.create_channel
    q  = ch.queue("", :auto_delete => true)

    raised = nil
    begin
      q.bind("asyd8a9d98sa73t78hd9as^&&(&@#(*^")
    rescue MarchHare::NotFound => e
      raised = e
    end

    raised.channel_close.reply_text.should =~ /no exchange/
  end
end
```

MarchHare Ruby exceptions follow AMQP 0.9.1 exception code names:

 * `MarchHare::NotFound`
 * `MarchHare::PreconditionFailed`
 * `MarchHare::ResourceLocked`
 * `MarchHare::AccessRefused`

or have otherwise meaningful names that follow [Bunny](http://rubybunny.info) names closely:

 * `MarchHare::PossibleAuthenticationFailureError`
 * `MarchHare::ChannelAlreadyClosed`


## MarchHare::Queue#subscribe Now Returns a Consumer

**This is a breaking API change**

`MarchHare::Queue#subscribe` now returns a consumer (a `MarchHare::Consumer` instance)
that can be cancelled and contains a consumer tag.

`MarchHare::Subscription` was eliminated as redundant. All the same methods are
now available on `MarchHare::Consumer` subclasses.


## MarchHare::Queue#subscribe Uses :block => false By Default

**This is a breaking API change**

`MarchHare::Queue#subscribe` now uses `:block => false` by default, thus
not blocking the caller. This reduces the need to use explicitly
started threads for consumers.

This is also how Bunny 0.9 works and we've seen this default to be
a better idea.


## More Convenient Way of Creating Thread Pools

MarchHare allows you to pass your own thread pool to `MarchHare::Queue#subscribe` via
the `:executor` option. Choosing the right thread pool size can make a huge difference
in throughput for applications that use non-blocking consumers.

Previously to 2.0, MarchHare required using Java interop and being familiar
with JDK executors API to instantiate them.

MarchHare 2.0 introduces `MarchHare::ThreadPools` that has convenience methods
that make it easier:

``` ruby
# fixed size thread pool of size 1
MarchHare::ThreadPools.single_threaded
# fixed size thread pool of size 16
MarchHare::ThreadPools.fixed_of_size(16)
# dynamically growing thread pool, will allocate new threads
# as needed
MarchHare::ThreadPools.dynamically_growing

# in context
subscribe(:blocking => false, :executor => MarchHare::ThreadPools.single_threaded) do |metadata, payload|
 # ...
end
```


## RabbitMQ Java Client Upgrade

March Hare now uses RabbitMQ Java client 3.2.


## Queue Predicates

`MarchHare::Queue` now provides several predicate methods:

 * `#server_named?`
 * `#auto_delete?`
 * `#durable?`
 * `#exclusive?`

for better [Bunny 0.9](http://rubybunny.info)+ compatibility.

## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
