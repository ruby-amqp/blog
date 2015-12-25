---
layout: post
title: "Hutch 0.20.0 is Released"
date: 2015-11-16 09:15
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.20.0](https://rubygems.org/gems/hutch/versions/0.20.0) is released to rubygems.org.

This is a minor feature release.


## Changes between 0.19.0 and 0.20.0

### Hutch::Exception includes Bunny::Exception

`Hutch::Exception` now inherits from `Bunny::Exception` which
inherits from `StandardError`.

GH issue: [#137](https://github.com/gocardless/hutch/issues/137).


### Pluggable (Negative) Acknowledge Handlers

Hutch now can be configured to use a user-provided
object(s) to perform acknowledgement on consumer exceptions.

For example, this is what the default handler looks like:

``` ruby
require 'hutch/logging'
require 'hutch/acknowledgements/base'

module Hutch
  module Acknowledgements
    class NackOnAllFailures < Base
      include Logging

      def handle(delivery_info, properties, broker, ex)
        prefix = "message(#{properties.message_id || '-'}): "
        logger.debug "#{prefix} nacking message"

        broker.nack(delivery_info.delivery_tag)

        # terminates further chain processing
        true
      end
    end
  end
end
```

Handlers are configured similarly to exception notification handlers,
via `:error_acknowledgements` in Hutch config.

Contributed by Derek Kastner.

GH issue: [#177](https://github.com/gocardless/hutch/pull/177).


### Configurable Exchange Properties

`:mq_exchange_options` is a new config option that can be used
to provide a hash of exchange attributes (durable, auto-delete).
The options will be passed directly to Bunny (or March Hare, when
running on JRuby).

Contributed by Derek Kastner.

GH issue: [#170](https://github.com/gocardless/hutch/pull/170).


### Bunny Update

Bunny is updated to 2.2.1.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

