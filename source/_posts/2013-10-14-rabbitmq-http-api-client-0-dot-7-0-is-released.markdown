---
layout: post
title: "RabbitMQ HTTP API Client 0.7.0 is Released"
date: 2013-10-14 14:33
comments: false
categories:
  - rabbitmq_http_api_client
  - releases
---

Ruby RabbitMQ HTTP API client `0.7.0` is released.

This is a minor feature release.


## Changes Between 0.6.0 and 0.7.0

### Support for Basic HTTP Auth Credentials in URI

It is now possible to pass credentials in the endpoint URI:

``` ruby
c = RabbitMQ::HTTP::Client.new("https://guest:guest@127.0.0.1:15672/")
```


## Changes Between 0.5.0 and 0.6.0

### Support for Advanced Connection Options

It is now possible to pass more options to Faraday connection,
for example, HTTPS related ones:

``` ruby
c = RabbitMQ::HTTP::Client.new("https://127.0.0.1:15672/", username: "guest", password: "guest", ssl: {
  client_cer: ...,
  client_key: ...,
  ca_file:    ...,
  ca_path:    ...,
  cert_store: ...
})
```

Any options other than `username` and `password` will be passed on to
`Faraday::Connection`.



## Changes Between 0.4.0 and 0.5.0

### Endpoint Reader

`RabbitMQ::HTTP::Client#endpoint` is a new reader (getter) that makes
it possible to access the URI a client instance uses.




[Full change log](https://github.com/ruby-amqp/rabbitmq_http_api_client/blob/master/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
