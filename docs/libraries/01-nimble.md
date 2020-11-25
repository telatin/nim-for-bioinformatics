---
layout: default
title: Installing libraries with Nimble
parent: Libraries
nav_order: 1
---

# Installing libraries
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

[Nimble](https://github.com/nim-lang/nimble#readme) is the package manager for Nim.
It can be used to create packages and to simplify the distribution of your modules
and programs, but in this section I'll focus on its use as a package manager to
download and install Nim libraries.

## Installation

Nimble is bundled with Nim since version 0.15.0, and given that this document
is written for Nim 1.0+ we will assume it's already installed in your system.

## Refresh the package list

```bash
nimble refresh
```

## Search for a package

Google is probably the best way to check in advance if a module is well maintained
or provides the desired functionalities, the
**[nimble.directory](https://nimble.directory)**
website is a good catalogue for nim packages.

Nevertheless, if you need to make a quick
scan **nimble search** can be of some help:

```bash
nimble search csv
```

Will produce a list similar to:

```text
csv:
  url:         https://github.com/achesak/nim-csv (git)
  tags:        csv, parsing, stringify, library
  description: Library for parsing, stringifying, reading, and writing CSV (comma separated value) files
  license:     MIT
  website:     https://github.com/achesak/nim-csv

[...]

csvtable:
  url:         https://github.com/apahl/csvtable (git)
  tags:        csv, table
  description: tools for handling CSV files (comma or tab-separated) with an API similar to Python's CSVDictReader and -Writer.
  license:     MIT
  website:     https://github.com/apahl/csvtable
```

## Install a package

When the package name is available via nimble:

```bash
nimble install docopt
```

Sometimes, the **latest version** is not available via nimble, but it's only
available as the latest commit from the package's repository:

```bash
nimble install docopt@#head
```

Nimble allows to install from **URL**:

```bash
nimble install https://github.com/nimble-test/multi
```

...also from **subdirectories**:

```bash
nimble install https://github.com/nimble-test/multi?subdir=alpha
```
