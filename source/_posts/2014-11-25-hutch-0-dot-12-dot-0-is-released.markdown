---
layout: post
title: "Hutch 0.12.0 is Released"
date: 2014-11-25 14:53
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.12.0](https://rubygems.org/gems/hutch/versions/0.12.0) is released to rubygems.org.

This is primarily a bug fix release.


## Change Between 0.11.0 and 0.12.0

### Explicit Requires

Hutch no longer relies on `Kernel#autoload` to load its key
modules and classes.

Contributed by Pierre-Louis Gottfrois.


### hutch --version No Longer Fails

```
hutch --version
```

no longer fails with an exception.

Contributed by Olle Jonsson.


### Base Class for All Hutch Exceptions

All Hutch exceptions now inherit from `Hutch::Exception`.

Contributed by Pierre-Louis Gottfrois.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

