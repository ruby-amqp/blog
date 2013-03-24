---
layout: post
title: "amqp gem 1.0 is released"
date: 2013-03-24 20:00
comments: false
categories:
  - releases
  - "amqp gem"
---

> Give a programmer a ship and you excite him for a day. Teach him how to ship
> and you excite him for a lifetime.
>
> -- Lao Tzu

## TL;DR

[amqp gem 1.0.0](https://rubygems.org/gems/amqp/versions/1.0.0) is released to rubygems.org. The library
is almost 5 years old, has undergone a major refactoring in `0.8.x` and evolves like a mature project.
It's time to release `1.0`.

This release is 100% backwards compatible with `0.9.x` and includes no changes visible to library users.



## It's Time For 1.0

In the last year-and-a-half or so, [amqp gem](http://rubyamqp.info) has been evolving like a mature project for a while now. What does that mean?
A couple of things:

 * Things don't change often.
 * Most issues only affect a small % of users and almost always can be classified as edge cases,
   minor usability issues or Heisenbugs specific to certain systems.

In July 2013, amqp gem will turn 5 years old. It's a pretty significant age for a library. In these years
amqp gem has undergone a major rework in 2010-2011, got [pretty solid documentation guides](http://rubyamqp.info) written
and has been pretty well battle tested by small and large companies.

It's only natural to release `1.0.0` instead of bumping `0.9.x` patch levels until we reach `0.9.99`.


## Change log

`1.0.0` is based on the master branch which is completely backwards compatible with `0.9.x` but removes
some long deprecated API elements. In other words, if you are running [the most recent `0.9.x` release](http://blog.rubyrabbitmq.info/blog/2013/03/05/amqp-gem-0-dot-9-10-is-released/),
there is no change log :)

So go ahead and upgrade to `1.0`. It's in better shape than ever before and passed the test of time.



## The Future

Does it mean that the work on them gem is done? No, definitely not. RabbitMQ gets new features,
people suggest usability improvements and [Heisenbugs](http://en.wikipedia.org/wiki/Heisenbug) are discovered by large users every
so often.

So you can be sure that amqp gem and [its documentation](http://rubyamqp.info) will continue evolving.
To keep up-to-date with future releases, join [our mailing list](http://groups.google.com/group/ruby-amqp),
[RabbitMQ mailing list](https://lists.rabbitmq.com/cgi-bin/mailman/listinfo/rabbitmq-discuss) and [follow @rubyamqp](http://twitter.com/rubyamqp) on Twitter.



## Supported Ruby Versions

amqp gem `1.0` supports a range of Ruby versions and implementations:

 * CRuby 2.0
 * CRuby 1.9.3
 * CRuby 1.9.2
 * Rubinius 2.0 in both modes
 * JRuby 1.6+ in both modes
 * CRuby 1.8.7, REE



## Supported RabbitMQ Versions

amqp gem `1.0` requires RabbitMQ `2.0` or later. `3.x` releases are always recommended. Running
a recent Erlang/OTP release is also a good idea.



## Alternatives

If you are looking for a Ruby RabbitMQ client and amqp gem does not fit your bill, take a look at

 * [Bunny](http://rubybunny.info)
 * [Hot Bunnies](http://github.com/ruby-amqp/hot_bunnies) (JRuby-only)


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients Team](http://github.com/ruby-amqp)
