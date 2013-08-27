---
layout: post
title: "Bunny 0.10.4 is released"
date: 2013-08-26 13:01
comments: false
categories:
  - releases
  - bunny
---

## TL;DR

[Bunny 0.10.4](https://rubygems.org/gems/bunny/versions/0.10.4) is released to rubygems.org.

This is a usability improvements release that is **completely backwards compatible**
with `0.10.x`.

We encourage all Bunny users to upgrade to it.


## Changes between Bunny 0.10.3 and 0.10.4

### Default Paths for TLS/SSL CA's on All OS'es

Bunny now uses OpenSSL to detect default TLS/SSL CA's paths, extending
this feature to OS'es other than Linux.

Contributed by Jingwen Owen Ou.



## Changes between Bunny 0.10.2 and 0.10.3

### Default Paths for TLS/SSL CA's on Linux

Bunny now will use the following TLS/SSL CA's paths on Linux by default:

 * `/etc/ssl/certs/ca-certificates.crt` on Ubuntu/Debian
 * `/etc/ssl/certs/ca-bundle.crt` on Amazon Linux
 * `/etc/ssl/ca-bundle.pem` on OpenSUSE
 * `/etc/pki/tls/certs/ca-bundle.crt` on Fedora/RHEL

and will log a warning if no CA files are available via default paths
or `:tls_ca_certificates`.

Contributed by Carl Hörberg.


[Full change log](https://github.com/ruby-amqp/bunny/blob/0.10.x-stable/ChangeLog.md) can be found on GitHub.


[Michael](http://twitter.com/michaelklishin) on behalf of the [Ruby RabbitMQ Clients](http://github.com/ruby-amqp) Team
