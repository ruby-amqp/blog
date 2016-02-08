---
layout: post
title: "Hutch 0.21.0 is Released"
date: 2016-02-08 14:52
comments: false
categories:
  - hutch
  - releases
---

## TL;DR

[Hutch 0.21.0](https://rubygems.org/gems/hutch/versions/0.21.0) is released to rubygems.org.

This is a bug fix release.


## Changes Between 0.20.0 and 0.21.0 (February 7th, 2016)

### JRuby Compatibility Restored

Contributed by Jesper Josefsson.

### More Reliable Rails app Detection

Rails application detection now won't produce false positives
for applications that include `config/environment.rb`. Instead,
`bin/rails` and `script/rails` are used.

Contributed by @bisusubedi.

### Refactoring

Contributed by Jesper Josefsson and Olle Jonsson.



## Full Changelog

[Full change log](https://github.com/gocardless/hutch/blob/master/CHANGELOG.md) can be found on GitHub.



## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the Hutch maintainers Team.

