---
layout: post
title: "Bunny 0.9.0.pre13 is released"
date: 2013-05-30 19:18
comments: false
categories:
  - bunny
  - releases
---

## TL;DR

[Bunny 0.9.0.pre13](https://rubygems.org/gems/bunny/versions/0.9.0.pre13) is released to rubygems.org.

This release fixes a regression that affected consumers and a few minor usability improvements
for "one-off" consumers that cancel themselves.


## Changes between Bunny 0.9.0.pre12 and 0.9.0.pre13

### Channels Without Consumers Now Tear Down Consumer Pools

Channels without consumers left (when all consumers were cancelled)
will now tear down their consumer work thread pools, thus making
`HotBunnies::Queue#subscribe(:block => true)` calls unblock.

This is typically the desired behavior.

### Consumer and Channel Available In Delivery Handlers

Delivery handlers registered via `Bunny::Queue#subscribe` now will have
access to the consumer and channel they are associated with via the
`delivery_info` argument:

``` ruby
q.subscribe do |delivery_info, properties, payload|
  delivery_info.consumer # => the consumer this delivery is for
  delivery_info.consumer # => the channel this delivery is on
end
```

This allows using `Bunny::Queue#subscribe` for one-off consumers
much easier, including when used with the `:block` option.

### Bunny::Exchange#wait_for_confirms

`Bunny::Exchange#wait_for_confirms` is a convenience method on `Bunny::Exchange` that
delegates to the method with the same name on exchange's channel.



## Plans for 0.9.0 Final

There is still a few things we need to do before Bunny 0.9 can be declared complete:

 * Fix any remaining important issues we get reports for
 * Finish TLS support



[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
