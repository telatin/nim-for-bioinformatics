---
layout: default
title: Print
parent: Language basics
nav_order: 1
---

# Print
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## echo, the smart print()

In our [Hello world]({{ site.baseurl }}{% link docs/hello-world.md %}) example
we had to print a text, and we used the `echo` identifier, that is automatically
imported (and it's part of the [system](https://nim-lang.org/docs/system.html) module).

`echo` will automatically convert the arguments to string, and will add a new line
at the end. In the following example we print strings (surrounded by double quotes),
a string variable, an integer (returned from the `len()` function) and even a sequence
(list):

```nim
var
  package = "samtools"
  versions = @[0.19, 1.0, 1.4]

echo "We have ", len(versions), " versions of ", package, ": ", versions
```

The output would be:
```text
We have 3 versions of samtools: @[0.19, 1.0, 1.4]
```

### Converting to string

The `$` operator will convert to string it's operand. `echo` effectively uses this
operator when receiving its typed arguments (in other words, trying to print
a type that does not have an overloaded `$` will fail).

In the following example we use the concatenation
operator (`&`, see [strings]()) and the conversion to string to produce to produce
a string, called _packageString_, having as content "_samtools 0.19_":

```nim
var
  package = "samtools"
  versions = @[0.19, 1.0, 1.4]
  packageString = package & " " & $versions[0]

echo packageString
```

## Print to standard error and standard output

`stdout.writeLine` and `stderr.writeLine` will print, respectively, to the
**standard output** and to the **standard error**. They will not add a newline.
