# uri

A `URI` datatype and parser for Carp.

## Installation

````clojure
(load "git@github.com:carpentry-org/uri@0.0.1
```

## Usage

To get started, you’ll most probably want to parse a `URI` from a string. To do
so, you use `URI.parse`. This function will return a `URI` datatype for you to
work with, or an error type if the URI string was invalid.

If you havea a URI value the simplest operation is probably converting the URI
back to a string using the `str` interface, which should be idempotent—i.e.
you’ll get the original URI back.

You can also ask the `URI` for its properties, like the scheme, the port, or the
URI parameters.

A more complete documentation can be found under [https://veitheller.de/uri/](https://veitheller.de/uri)!

<hr/>

Have fun!
