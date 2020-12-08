---
layout: default
title: Installing libraries with Nimble
parent: Standard modules
nav_order: 2
---

# Standard modules
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

As we saw in the previous parts, sometimes we need to import modules to extend
the capabilities of the language.
There are modules that will come with nim, and they compose the
[standard library](https://nim-lang.org/docs/lib.html).
Externally developed libraries can also be installed, as we will see later.

Some important libraries of the standard library are:

## Core modules
- system (imported by default)
  - threads (imported by default, but requires `--threads:on` when compiling)
  - channels (imported by default, but requires `--channels:on` when compiling)
- threadpool

## Collections and algorithms
- algorithm (to import sorting functions for example)
- tables
- sets
- sequtils

## Strings
- strutils
- strformat
- parseutils
- strtabs
- unicode
- pegs

## Operating system
- os
- osproc
- times
- asyncfile (asynchronous file reading and writing using asyncdispatch)

## Parsers
- parseopt (this is the bundled module for parsing command line arguments, but there are several alternatives)
- parsecfg
- json
- xmlparser
- htmlparser
