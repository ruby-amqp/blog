---
layout: post
title: "rabbitmq_http_api_client 0.4.0 is released"
date: 2013-09-17 09:54
comments: false
categories:
  - rabbitmq_http_api_client
  - releases
---

Ruby RabbitMQ HTTP API client `0.4.0` is released.

This is a minor feature release that changes the way `4xx` and
`5xx` responses are handled.


## Changes Between 0.3.0 and 0.4.0

### Meaningful Exceptions for 4xx and 5xx Responses

`4xx` and `5xx` responses now will result in meaningful exceptions
being raised. For example, `404` responses will raise `Faraday::Error::ResourceNotFound`.




[Full change log](https://github.com/ruby-amqp/rabbitmq_http_api_client/blob/master/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
