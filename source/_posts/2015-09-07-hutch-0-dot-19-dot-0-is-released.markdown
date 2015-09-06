---
layout: post
title: "Hutch 0.19.0 is Released"
date: 2015-09-07 00:41
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.19.0](https://rubygems.org/gems/hutch/versions/0.19.0) is released to rubygems.org.

This is a minor feature release.


## Changes Between 0.18.0 and 0.19.0

### Pluggable Serialisers

Hutch now supports pluggable serialisers: see `Hutch::Serializer::JSON` for
an example. Serialiser is configured via Hutch config as a Ruby
class.

Contributed by Dmitry Galinsky.


### multi_json Update

Hutch now depends on multi_json `1.11.x`.

### Bunny Update

Bunny is updated to [2.2.0](http://blog.rubyrabbitmq.info/blog/2015/09/06/bunny-2-dot-2-0-is-released/).

### More Bunny SSL Options

`:mq_tls_ca_certificates` and `:mq_verify_peer` options will now be passed on to Bunny as `:tls_ca_certificates` and `:verify_peer` respectively.

Contributed by Kennon Ballou.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

