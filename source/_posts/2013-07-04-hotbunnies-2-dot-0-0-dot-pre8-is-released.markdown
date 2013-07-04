---
layout: post
title: "HotBunnies 2.0.0.pre8 is released"
date: 2013-07-04 17:37
comments: false
categories:
  - hot_bunnies
  - jruby
  - releases
---

## TL;DR

[HotBunnies 2.0.0.pre8](https://rubygems.org/gems/hot_bunnies/versions/2.0.0.pre8) is released to rubygems.org.

This release is a development milestone. 2.0 focuses on usability and introduces a couple of
major API improvements and features.

2.0 should be production ready from the stability perspective but has **breaking API changes**.
Please consult the change log below before considering upgrading.


# Changes Between 1.5.0 and 2.0.0

Hot Bunnies 2.0 has **breaking API changes**.

## Shutdown Callbacks

`HotBunnies::Session#on_shutdown` and `HotBunnies::Channel#on_shutdown` are two
new methods that register **shutdown hooks**. Those are executed when

 * Network connectivity to RabbitMQ is lost
 * RabbitMQ shuts down the connection (because of an error or management UI action)

The callbacks take two arguments: the entity that's being shutdown
(`HotBunnies::Session` or `HotBunnies::Channel`) and shutdown reason (an exception):

``` ruby
conn = HotBunnies.connect
conn.on_shutdown |conn, reason|
  # ...
end
```

In addition, HotBunnies channels will make sure consumers are gracefully
shutdown (thread pools stopped, blocking consumers unblocked).

These are initial steps towards easier to use error handling and recovery,
similar to what amqp gem and Bunny 0.9+ provide.


## HotBunnies::Session#start

`HotBunnies::Session#start` is a new no-op method that improves API
compatibility with [Bunny 0.9](http://rubybunny.info).

## HotBunnies::Queue#subscribe_with, HotBunnies::Queue#build_consumer

`HotBunnies::Queue#subscribe_with` and `HotBunnies::Queue#build_consumer` are new method
that allow using consumer objects, for example, to first instantiate a blocking consumer
and pass the reference around so it can be cancelled from a different thread later.

``` ruby
consumer_object  = q.build_consumer(:blocking => false) do |metadata, payload|
  # ...
end
consumer         = q.subscribe_with(consumer_object, :blocking => false)
```


## Consumer Cancellation Support

Passing a block for the `:on_cancellation` option to `HotBunnies::Queue#subscribe`
lets you support [RabbitMQ consumer cancellation](http://www.rabbitmq.com/consumer-cancel.html). The block should take 3
arguments: a channel, a consumer and a consumer tag.


## HotBunnies Operations Now Raise Ruby Exceptions

HotBunnies used to expose RabbitMQ Java client's channel implementation
directly to Ruby code. This means that whenever an exception was raised,
it was a Java exception (commonly `java.io.IOException`, wrapping a shutdown
signal).

Not only this severely violates the Principle of Least Surprise, it also
makes it much harder to inspect the exception and figure out how to get
relevant information from it without reading the RabbitMQ Java client
source.

Hot Bunnies 2.0+ provides a Ruby implementation of `HotBunnies::Channel`
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
    rescue HotBunnies::NotFound => e
      raised = e
    end

    raised.channel_close.reply_text.should =~ /no exchange/
  end
end
```

HotBunnies Ruby exceptions follow AMQP 0.9.1 exception code names:

 * `HotBunnies::NotFound`
 * `HotBunnies::PreconditionFailed`
 * `HotBunnies::ResourceLocked`
 * `HotBunnies::AccessRefused`

or have otherwise meaningful names that follow [Bunny](http://rubybunny.info) names closely:

 * `HotBunnies::PossibleAuthenticationFailureError`
 * `HotBunnies::ChannelAlreadyClosed`


## HotBunnies::Queue#subscribe Now Returns a Consumer

**This is a breaking API change**

`HotBunnies::Queue#subscribe` now returns a consumer (a `HotBunnies::Consumer` instance)
that can be cancelled and contains a consumer tag.

`HotBunnies::Subscription` was eliminated as redundant. All the same methods are
now available on `HotBunnies::Consumer` subclasses.


## HotBunnies::Queue#subscribe Uses :block => false By Default

**This is a breaking API change**

`HotBunnies::Queue#subscribe` now uses `:block => false` by default, thus
not blocking the caller. This reduces the need to use explicitly
started threads for consumers.

This is also how Bunny 0.9 works and we've seen this default to be
a better idea.


## RabbitMQ Java Client Upgrade

Hot Bunnies now uses RabbitMQ Java client 3.1.




## Plans for 2.0.0 Final

There is still a few things we need to do before HotBunnies 2.0 can be declared complete:

 * Investigate automatic network failure recovery, like Bunny 0.9
 * Make TLS support more configurable, ideally with the same API as Bunny 0.9
 * Add logging
 * API reference documentation


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
