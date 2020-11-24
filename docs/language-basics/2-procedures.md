---
layout: default
title: Procedures (functions)
parent: Language basics
nav_order: 3
---

# Procedures (functions)
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

What Python calls functions (and Perl subroutines) is called **procedure** in Nim.
A function will process some input parameters and will eventually return some output.
In Nim you must specify the type of each parameter as well as the type of the returned output.

Let's just start with a couple of simple procedures, defined after a **proc** keyword:

```nim
# proc <name>(<p1>: <type1>, <p2>: <type2>, ...): <returnType>

proc CombineStrings(a, b: string): string =
  # will return the concatenation of two strings, separating them with a dash
  return a & "-" & b

proc SumIntegers(a, b: int): int =
  return a + b
```

Note that you list the input parameters in brakets specifying their type, and then you have to specify the type returned by the procedure (if any).

## The "result" variable

very procedure has an implicit variable called `result` that stores the result,
and it's automatically initialized with the correct type (what the procedure will return):
```nim
proc addPolyA(sequence: string, length: int): string =
  result = sequence
  for i in 1 .. length:
    result &= "A"            # This is a shortcut for result = result & 'A'

echo addPolyA("CAGATA", 20)

```

## Discarding the result

If your procedure is defined to produce some output, but you don't make use of it,
this will result in an error.
If you want to allow the result to be discarded,
add `{.discardable.}` to the declaration:

```nim
# In nim you concatenate strings with "&",
# but you can define that "+" is good too. In this case we add a space between.
proc `+`(a, b: string): string =
 a & " " & b

echo "Hello," + "world!"
```

## Generics
Generic functions (similar to C++ templates)
will allow to define operators for specific types (mainly custom):

```nim
# In nim you concatenate strings with "&",
# but you can define that "+" is good too. In this case we add a space between.
proc `+`(a, b: string): string =
 a & " " & b

echo "Hello," + "world!"
```
