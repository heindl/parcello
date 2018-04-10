# Embedo

[![Documentation][godoc-img]][godoc-url]
![License][license-img]
[![Build Status](https://travis-ci.org/phogolabs/embedo.svg?branch=master)](https://travis-ci.org/phogolabs/embedo)

An embeddable resource manager for Golang

## Overview

Embedo is a simple resource manager for Golang that allows embedding artefacts
like SQL and bash scripts. That allows easy release management by deploying
just a single binary rather than many files.

## Installation

```console
$ go get -u github.com/phogolabs/embedo
$ go install github.com/phogolabs/embedo/cmd/embedo
```

## Usage

The best way to use the tool is via `go generate`. In order to embed all
resource in particular directory, you should make it a package that has the
following comment:

```golang
// Package database contains the database artefacts of GOM as embedded resource
package database

//go:generate embedo -r -d .
```

When you run:

```console
$ go generate ./...
```

The tools will create a `resource.go` file that contains
all embedded resource in that directory and its
subdirectories.

You can read the content in the following way:

```golang
file, err := database.ResourceManager.Open("your_subdirectory/your_file.")
```

## Contributing

We are welcome to any contributions. Just fork the
[project](https://github.com/phogolabs/embedo).

[embedo-url]: https://github.com/phogolabs/embedo
[godoc-url]: https://godoc.org/github.com/phogolabs/embedo
[godoc-img]: https://godoc.org/github.com/phogolabs/embedo?status.svg
[license-img]: https://img.shields.io/badge/license-MIT-blue.svg
[software-license-url]: LICENSE
