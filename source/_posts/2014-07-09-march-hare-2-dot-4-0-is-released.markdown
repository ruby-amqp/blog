---
layout: post
title: "March Hare 2.4.0 is released"
date: 2014-07-09 12:13
comments: false
categories:
  - march_hare
  - jruby
  - releases
---

## TL;DR

[March Hare 2.4.0](https://rubygems.org/gems/march_hare/versions/2.4.0) is
released to rubygems.org.

This is a minor feature release.



### MarchHare::Exchange#publish Options Bunny Compatibility

`MarchHare::Exchange#publish` now accepts property options the same way
as [Bunny](http://rubybunny.info) does (the old way with the `:properties`
option is still supported). This improves March Hare and Bunny API compatibility.

The new way:

``` ruby
exchange.publish(payload,
                 :app_id      => "hotbunnies.tests",
                 :persistent  => true,
                 :priority    => 8,
                 :type        => "kinda.checkin",
                 # headers table keys can be anything
                 :headers     => {
                   "coordinates" => {
                     "latitude"  => 59.35,
                     "longitude" => 18.066667
                   },
                   "time"         => @now,
                   "participants" => 11,
                   "venue"        => "Stockholm",
                   "true_field"   => true,
                   "false_field"  => false,
                   "nil_field"    => nil,
                   "ary_field"    => ["one", 2.0, 3, [{ "abc" => 123 }]]
                 },
                 :timestamp        => @now,
                 :reply_to         => "a.sender",
                 :correlation_id   => "r-1",
                 :message_id       => "m-1",
                 :content_type     => "application/octet-stream",
                 # just an example. MK.
                 :content_encoding => "zip/zap",
                 :routing_key    => "hotbunnies.key")
```

The old way:

``` ruby
exchange.publish(payload,
                 :properties => {
                   :app_id      => "hotbunnies.tests",
                   :persistent  => true,
                   :priority    => 8,
                   :type        => "kinda.checkin",
                   # headers table keys can be anything
                   :headers     => {
                     "coordinates" => {
                       "latitude"  => 59.35,
                       "longitude" => 18.066667
                     },
                     "time"         => @now,
                     "participants" => 11,
                     "venue"        => "Stockholm",
                     "true_field"   => true,
                     "false_field"  => false,
                     "nil_field"    => nil,
                     "ary_field"    => ["one", 2.0, 3, [{ "abc" => 123 }]]
                   },
                   :timestamp        => @now,
                   :reply_to         => "a.sender",
                   :correlation_id   => "r-1",
                   :message_id       => "m-1",
                   :content_type     => "application/octet-stream",
                   # just an example. MK.
                   :content_encoding => "zip/zap"
                 },
                 :routing_key    => "hotbunnies.key")
```

Contributed by Devin Christensen.


## Full Change Log

Please consult the [change log](https://github.com/ruby-amqp/march_hare/blob/master/ChangeLog.md)
to learn about the changes.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
