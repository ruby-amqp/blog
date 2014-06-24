---
layout: post
title: "amqp gem 1.4.0 is Released"
date: 2014-06-24 09:04
comments: false
categories:
  - "amqp gem"
  - releases
---

## TL;DR

[amqp gem 1.4.0](https://rubygems.org/gems/amqp/versions/1.4.0) is released to rubygems.org.

This release includes a minor feature.


## Changes Between 1.3.x and 1.4.0

### connection.blocked Support

[connection.blocked](https://www.rabbitmq.com/connection-blocked.html) notifications
are now correctly supported by the library:

``` ruby
EventMachine.run do
  connection = AMQP.connect(:host => '127.0.0.1')

  connection.on_blocked do |conn, conn_blocked|
    puts "Connection blocked, reason: #{conn_blocked.reason}"
  end

  connection.on_unblocked do |conn, _|
    puts "Connection unblocked"
  end
end
```



## Full Change Log

[Full change log](https://github.com/ruby-amqp/amqp/blob/1.4.x-stable/ChangeLog.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
