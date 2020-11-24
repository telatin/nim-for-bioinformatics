---
layout: default
title: Getting Started with Variables
parent: Language basics
nav_order: 2
---

# Buttons
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Indentation
Nim has a Python like code block structure, that means that we will use indentation to specify which statements are nested, but it's more stringent in **requiring spaces** and disallowing tabs.

```python
#[
  you can put multiline comments between
  hash plus square brackets
]#

var line = "@AT_1"

if line[0] == '@':
  echo "Sequence name: ", line[1 .. line.high]
else:
  echo "Not a sequence name..."
```

## Basic types
In the intentation example we introduced our first variable, called line, that is a string. These are the basic types in Nim that are automatically imported:

| Type           | Description    | Example    |
+----------------+----------------+------------+
| int            | Integer numbers | `var threads = 8`  |
| float          | Numbers with a decimal point  | `var quasiPi = 3.15`  |
| char |  A single ASCII character   | `var fastqHead = '@'` |
| string  | A string of text (multiple chars)  | `var msg = "Hello"`  |
| bool    | True or False                      | `var debug = false`  |

There are more [primitive types](https://nim-by-example.github.io/primitives/), but these are the easiest to use.

## Declaring variables
In the example we used the var keyword to declare a variable:

```python
var line = "@AT_1"  # this is a string
```

We created and initialized a variable of type string, and we didn't need to specify the type as this is auto-inferred by the value. If we want to create a variable without initializing it, we must specify its value:

```python
var line: string
```

We can declare and/or initialize multiple variables with a single var statement:

```python
var
  line = "this line"
  delim = ','
  debug = true
  count : int
```

The last variable, count, is declared but had no value assigned to it.

:information: Identifiers in Nim are style insensitive.
This is an interesting - and potentially confusing - feature that makes a variable called `id_string`
to be callable as `idString`. Even if it was declared in "snake  style" it can be accessed in "camelCase".

## Types of variables

Variable as very common in any scripting language, but their immutable siblings are less known:

| Type           | Keyword    |  
+----------------+----------------+
| Variable (it's value can change)            | **var** |
| Immutable variable (cannot change)          | **let** |
| Constant (cannot change and must be computed at compile time) | **const** |

If you have a piece of information that will _not_ need to change its value during the program execution, it's wise to use _let_ or _const_ to store it.
This will prevent unwanted behaviours and will provide some extra speed.
You can use const only if the value can be known at compile time (for example, you know that FASTQ sequences start by `@`),
while you'll need to use _let_ for immutable variables that will get their first value assigned at runtime
(for example, a parameter supplied by the user).  

:information: If you have a function returning a value, it can be used to assign a value to a constant. The function will be executed at compile time.

## Some examples
Variables are supposed to change their value during the program execution:

```python
# Declaring multiple variables, initializing them
var
  name = "Andrea"
  lang = "nim"

# Declaring uninitialized variables
var
  name: string
  age: int
  height: float
```

Immutable variables will contain constants or values that will not change during the program execution:

```python
let
  pi = 3.1415
  progName = "Cottage Pi"
  progVer = "0.1.0"
```

We will see more about [strings]({{ site.baseurl }}{% link docs/language-basics/variables.md %}) later,
as well as more complex data structures (
[arrays and sequences]({{ site.baseurl }}{% link docs/language-basics/variables.md %}) and
[tables]({{ site.baseurl }}{% link docs/language-basics/variables.md %})
),
but first it's worth introducing some other basics concepts that will be very
easy to pick coming from any other programming language:
[procedures]({{ site.baseurl }}{% link docs/language-basics/variables.md %}) (functions) and
[control flow]({{ site.baseurl }}{% link docs/language-basics/variables.md %}) (if, for...).
