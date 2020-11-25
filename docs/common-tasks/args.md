---
layout: default
title: Command line arguments
parent: Common tasks
nav_order: 1
---

# Command line arguments
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

The standard library provides a basic library called **parseopt** to parse command line strings.
There are several alternatives (easily installed via _nimble_),
and here I'll show two that can be interesting:

 - **cligen**, that converts your procedure's expected parameters in the program's documentation (useful for quick prototyping).
 - **docopt**, that allows you to write the documentation and will parse it to retreive the command line parameters you need (available also for Python and other programming languages, see http://docopt.org/).

## parseopt (standard library)

The standard library provides a very basic options parser: _parseopt_.
It's quite a basic library, so I'll just place an example here. I personally
consider the user interface (the _command line interface_, in this case) to
be a critical aspect of your programs, so I would recommend using more sophisticated
libraries, but being installed by default it's worth knowing that it exists.

The main limitation of _parseopt_ is that it only supports the `--key=value` syntax and not the `--key valueone`.

```nim
import parseopt
import os
from strutils import parseint

# Prints version
proc writeVersion() =
  echo getAppFilename().extractFilename(), "0.1.0"

# Print help and exit
proc writeHelp() =
  writeVersion()
  echo """

  -h, --help        : show help
  -v, --version     : show version
  -m, --message STR : Message
  -t, --times INT   : Repeat message INT times
  """
  quit()

proc cli() =
  # Directly accessing the app name and parameters
  echo "# Program name: ", getAppFilename().extractFilename()
  echo "# Number of Parameters: ", paramCount()

  # Print all the parameters by index
  for paramIndex in 1 .. paramCount():    
    echo "# Raw param: ", paramIndex, ": ", paramStr(paramIndex)

  echo "---"

  var
    argCtr : int
    message: string
    times = 1
    i = 0

  # Loop trough all arguments
  for kind, key, value in getOpt():
    case kind

    # Positional arguments
    of cmdArgument:
      echo "# Positional argument ", argCtr, ": \"", key, "\""
      argCtr.inc

    # Switches
    of cmdLongOption, cmdShortOption:
      case key
      of "v", "version":
        writeVersion()
        quit()
      of "h", "help":
        writeHelp()
      of "m", "message":
        message = value
      of "t", "times":
        times = parseInt(value)
      else:
        echo "Unknown option: ", key

    of cmdEnd:
      discard

  if len(message) == 0:
    echo "No message specified :("

  while i < times:
    echo message
    i += 1

when isMainModule:
  cli()
```

## docopt


If you never used a _docopt_ inspired library (yes, there's a Python docopt too),
I recommend you have a look at their brilliant
[introductory video](https://www.youtube.com/watch?v=pXhcPJK5cMc#action=share) first.
The documentation is available at their [GitHub repository](https://github.com/docopt/docopt.nim)
and of course you
first need to install the library with `nimble install docopt` being a non standard library.

Reading the documentation is the best way to have a look at all the features,
and here I report a simple example:

```nim
import  docopt
const doc = """
CoolSeq - a program to do things

Usage:
  args_docopt status
  args_docopt list
  args_docopt analyse <directory> <database> [-o|--output=<outputFile>]

Options:
  status                      Check API Status
  list                        Check Result List
  convert                     Upload Images, convert to PDF and download result.pdf
  <directory>                 Specify directory with input files
  <database>                  Reference database
  -o, --output=<outputFile>   Output filename [default: result.bam]
"""

proc main() =
  let args = docopt(doc, version = "1.0")
  if args["status"]:
    echo "So you want to know the status! OK!"
  if args["list"]:
    echo "This is the list... finished!"
  if args["analyse"]:
    echo "CONVERTING:"
    echo "Directory: ", $args["<directory>"]
    echo "Reference: ", $args["<database>"]
    echo "Output:    ", $args["--output"] # note the default!

when isMainModule:
  main()
```

## cligen

While docopt let you write the documentation and will take care of parsing
the command line arguments accordingly, cligen does the opposite:
you code the required parameters and will dispatch the documentation for the user.
It will automatically include a `--help` switch for you, and unlike parseopt will
also recognize `--db name` (without the equal sign).
Also cligen requires installation via `nimble install cligen`.

```nim
import strutils, os

proc compareQueryWithDb(query, db: string, kmer = 8, complement = false) =
  let progName = split(getAppFilename(), "/")[getAppFileName().count("/")]

  if query != "" and db != "":
    echo "Query: ", query
    echo "Database: ", db
    echo "K-mer size: ", kmer
    echo "Complement: ", complement
  else:
    echo "ERROR\n", progName, " needs query and target filenames..."

when isMainModule: import cligen;dispatch(compareQueryWithDb)
```
