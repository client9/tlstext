# tlstext 

[![Build Status](https://travis-ci.org/signalsciences/tlstext.svg?branch=main)](https://travis-ci.org/signalsciences/tlstext) [![Go Report Card](http://goreportcard.com/badge/signalsciences/tlstext)](http://goreportcard.com/report/signalsciences/tlstext) [![GoDoc](https://godoc.org/github.com/signalsciences/tlstext?status.svg)](https://godoc.org/github.com/signalsciences/tlstext) [![Coverage](http://gocover.io/_badge/github.com/signalsciences/tlstext)](http://gocover.io/github.com/signalsciences/tlstext) [![license](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)](https://raw.githubusercontent.com/signalsciences/tlstext/main/LICENSE)


simple mapping of TLS Versions and Cipher Suites to strings

The [Go TLS cipher suites and TLS versions](http://golang.org/pkg/crypto/tls/#pkg-constants) are untyped
or are `uint16` and without a string representation.  This also means
the tool [stringer](https://godoc.org/golang.org/x/tools/cmd/stringer)
can not be used.

This package provides simple functions `tlstxt.Version` and
`tlstext.CipherSuite` that provide the raw value to string translations.

This intentionally does not use the constants in
[tls/cipher_suites.go](https://golang.org/src/crypto/tls/cipher_suites.go)
since they are dependent on the version of Go used.

The values are generated directly from the [IANA assignments](http://www.iana.org/assignments/tls-parameters/tls-parameters.xml#tls-parameters-4)


## :rotating_light: NOTICE :rotating_light:

Effective **May 17th 2021** the default branch will change from `master` to `main`. Run the following commands to update a local clone:
```
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```
## Examples

Get string name from binary TLS version:

```
fmt.Println(tlstext.Version(uint16(0x0303)))
```

Output:

```
TLS12
```

Get cipher suite name:

```
fmt.Println(tlstext.CipherSuite(uint16(0xc02b)))
```

Output:

```
TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
```
