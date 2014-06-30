---
layout: post
title: "March Hare 2.3.0 is released"
date: 2014-06-30 11:11
comments: false
categories:
  - march_hare
  - releases
  - jruby
---

## TL;DR

[March Hare 2.3.0](https://rubygems.org/gems/march_hare/versions/2.3.0) is
released to rubygems.org.

This is a minor feature release.


## Changes Between 2.2.x and 2.3.0

### Custom Exception Handler Support

March Hare now provides a way to define a custom (unexpected) exception handler
RabbitMQ Java client will use:

``` ruby
class ExceptionHandler < com.rabbitmq.client.impl.DefaultExceptionHandler
  include com.rabbitmq.client.ExceptionHandler

  def handleConsumerException(ch, ex, consumer, tag, method_name)
    # ...
  end
end

MarchHare.connect(:exception_handler => ExceptionHandler.new)
```

An exception handler is an object that conforms to the `com.rabbitmq.client.ExceptionHandler`
interface.


### Custom Thread Factories Support

Certain environments (e.g. Google App Engine) restrict thread modification.
RabbitMQ Java client 3.3 can use a custom factory in those environments.

March Hare now exposes this functionality to Ruby in a straightforward way:

``` ruby
java_import com.google.appengine.api.ThreadManager

MarchHare.connect(:thread_factory => ThreadManager.background_thread_factory)
```

A thread factory is an object that conforms to the [j.u.c.ThreadFactory](http://docs.oracle.com/javase/7/docs/api/java/util/concurrent/ThreadFactory.html)
interface:

``` ruby
class ThreadFactory
  include java.util.concurrent.ThreadFactory

  def newThread(runnable)
    # e.g. java.lang.Thread.new(runnable)
  end
end
```

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.3.4`.



## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
