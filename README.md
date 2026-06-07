# uri

is a `URI` datatype and parser for Carp.

## Installation

```clojure
(load "git@github.com:carpentry-org/uri@0.2.0")
```

## Usage

To get started, you’ll most probably want to parse a `URI` from a string. To do
so, you use `URI.parse`. This function will return a `URI` datatype for you to
work with, or an error type if the URI string was invalid.

If you have a a URI value the simplest operation is probably converting the URI
back to a string using the `str` interface, which should be idempotent—i.e.
you’ll get the original URI back.

You can also ask the `URI` for its properties, like the scheme, the port, or the
URI parameters.

### Resolving relative references

`URI.resolve` resolves a relative URI reference against a base URI, following
[RFC 3986 section 5](https://www.rfc-editor.org/rfc/rfc3986#section-5):

```clojure
(def base (Result.unsafe-from-success (URI.parse "http://a/b/c/d;p?q")))
(URI.resolve &base "../g")   ; => Success http://a/b/g
(URI.resolve &base "/g")     ; => Success http://a/g
(URI.resolve &base "?y")     ; => Success http://a/b/c/d;p?y
(URI.resolve &base "//h/p")  ; => Success http://h/p
```

`URI.remove-dot-segments` is the underlying path normalizer (RFC 3986 section
5.2.4). It resolves `.` and `..` segments in a path string:

```clojure
(URI.remove-dot-segments "/a/b/c/./../../g") ; => "/a/g"
```

A more complete documentation can be found under [https://veitheller.de/uri/](https://veitheller.de/uri)!

## Acknowledgements

This datatype and parser was heavily inspired by the one in [the Crystal
standard library](https://github.com/crystal-lang/crystal/blob/master/src/uri.cr).
I cannot thank the people who worked on it enough; they saved me from going
through a lot of pain and suffering!

<hr/>

Have fun!
