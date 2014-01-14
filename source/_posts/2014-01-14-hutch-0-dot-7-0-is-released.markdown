---
layout: post
title: "Hutch 0.7.0 is Released"
date: 2014-01-14 15:02
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.7.0](https://rubygems.org/gems/hutch/versions/0.7.0) is released to rubygems.org.

This release introduces several minor new features.


## Changes Between 0.6.0 and 0.7.0

### Optional HTTP API Use

It is now possible to make Hutch [not use RabbitMQ HTTP
API](https://github.com/gocardless/hutch/pull/69) (e.g. when the
RabbitMQ management plugin that provides it is not available).


### Extra Arguments for Hutch::Broker#publish

Extra options [passed to `Hutch::Broker#publish` will now be propagated](https://github.com/gocardless/hutch/pull/61).


### Content-Type for Messages

Messages published with Hutch now have content type set
to `application/json`.


### Greater Heartbeat Interval

Hutch now uses heartbeat interval of 30, so heartbeats won't interfere with transfers
of large messages over high latency networks (e.g. between AWS availability regions).


### Custom Queue Names

It is now possible to [specify an optional queue name](https://github.com/gocardless/hutch/pull/49):

``` ruby
class FailedPaymentConsumer
  include Hutch::Consumer
  consume 'gc.ps.payment.failed'
  queue_name 'failed_payments'

  def process(message)
    mark_payment_as_failed(message[:id])
  end
end
```

### Global Properties for Publishers

[Global properties can now be specified](https://github.com/gocardless/hutch/pull/62) for publishing:

``` ruby
Hutch.global_properties = proc {
  { app_id: 'api', headers: { request_id: RequestId.request_id } }
}
```


[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

