---
layout: post
title: "amqp gem 0.9.10 is released"
date: 2013-03-05 14:05
comments: true
categories: 
---

## TL;DR

[amqp gem 0.9.10](https://rubygems.org/gems/amqp/versions/0.9.10) is released to rubygems.org.

This release includes one bug fix. It is 100% backwards
compatible.


## Change Log

### Delayed Queue Operations Now More Resilient to Race Conditions

With amqp gem, code like this

``` ruby
ch.queue("", :exclusive => true).bind(x).subscribe do |meta, payload|
  # ...
end
```

will delay `queue.bind` and `basic.consume` operations until after the server-generated queue name is known.

In some cases (e.g. WebSocket/RabbitMQ proxies), the channel may be closed before they all complete. This
results in a connection-level exception (unknown channel being used) which renders the entire connection
unusable.

Starting with amqp gem `0.9.10`, delayed operations have a guard that prevents them from being executed
if the channel is already closed.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
