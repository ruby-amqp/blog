---
layout: post
title: "Hutch 0.11.0 is Released"
date: 2014-11-14 16:32
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.11.0](https://rubygems.org/gems/hutch/versions/0.11.0) is released to rubygems.org.

This release introduces a minor feature.


## 0.11.0 — Nov 14th, 2014

### Publisher Confirms Support

`:force_publisher_confirms` is a new configuration option that forces `Hutch.publish` to wait
for a confirm for every message published. Note that this **will cause a significant drop in throughput**:

``` ruby
Hutch::Config.set(:force_publisher_confirms, true)
```

`Hutch::Broker#confirm_select` and `Hutch::Broker#wait_for_confirms` are new public API methods
that delegate to their respective `Bunny::Channel` counterparts. `Hutch::Broker#confirm_select`
can be used to handle confirms with a callback instead of waiting:

``` ruby
broker.confirm_select do |delivery_tag, multiple, nack|
  # ...
end
```


## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

