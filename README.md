go-socks
========

![Build status](https://github.com/bokysan/go-socks/workflows/Build%20and%20release/badge.svg) [![Latest commit](https://img.shields.io/github/last-commit/bokysan/go-socks)](https://github.com/bokysan/go-socks/commits/master) [![Latest release](https://img.shields.io/github/v/release/bokysan/go-socks?sort=semver&Label=Latest%20release)](https://github.com/bokysan/go-socks/releases) [![License](https://img.shields.io/github/license/bokysan/go-socks)](https://github.com/bokysan/go-socks/blob/master/LICENSE) [![Go Report Card](https://goreportcard.com/badge/github.com/bokysan/go-socks)](https://goreportcard.com/report/github.com/bokysan/go-socks) ![Go version](https://img.shields.io/github/go-mod/go-version/bokysan/go-socks)

**This is an active fork of [go-socks5 by armon](https://github.com/armon/go-socks5)**, as the mentioned
repository does not seem to be updated.

Notable changes:
- upgrade to Go 1.14 and move to [Go modules](https://blog.golang.org/using-go-modules)
- merge active pull requests ([#18](https://github.com/armon/go-socks5/pull/18), [#22](https://github.com/armon/go-socks5/pull/22),
  [#24](https://github.com/armon/go-socks5/pull/24), [#25](https://github.com/armon/go-socks5/pull/25),
  [#38](https://github.com/armon/go-socks5/pull/38))


This module provides a package which implements a [SOCKS4/ SOCKS5 server](http://en.wikipedia.org/wiki/SOCKS).
SOCKS (Secure Sockets) is used to route traffic between a client and server through an intermediate proxy layer. 
This can be used to bypass firewalls or NATs.

Features
========

The package has the following features:

* SOCKS4 and SOCKS5 support
* "No Auth" mode *or* User/Password authentication
* Support for `CONNECT` command
* Rules to do granular filtering of commands
* Custom DNS resolution
* Unit tests
* Support for socks4 if enabled

TODO
====

The package still needs the following:
* Support for the BIND command
* Support for the ASSOCIATE command


Example
=======

Below is a simple example of usage

```go
package main

import "github.com/bokysan/go-socks"

// Create a SOCKS5 server
conf := &socks5.Config{}
server, err := socks5.New(conf)
if err != nil {
  panic(err)
}

// Create SOCKS5 proxy on localhost port 8000
if err := server.ListenAndServe("tcp", "127.0.0.1:8000"); err != nil {
  panic(err)
}
```

