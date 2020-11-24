---
layout: default
title: Strings
parent: Language basics
nav_order: 5
---

# Buttons
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Strings

Being strings used a lot in bioinformatics, let's see some more details on how to declare and use them.

## String declaration
Long strings can benefit from the multiline declaration using triple quotes:

```nim
let  program_description = """
  This program will do things on
  your FASTQ files
"""
```

As usual, you'll find special escape sequences like `\n` for newline, `\t` for a tab-space,
and `\\` for the backslash itself.
If you need to escape too many characters, you can use the **raw string literal**
where you will use two double-quotes to have one, but you can avoid escape other entities:

```nim
var escaped_text = "I like \"quotes\" and many \\ backslashes (like \\n or \\t)"
var same_thing =  r"I like ""quotes"" and many \ backslashes (like \n or \t)"
```

## Manipulating strings

### String concatenation

The `&` operator will concatenate strings.
It's an unusual operator, so I gave him its own paragraph.

```nim
var name = "Andrea"
var greeting = "Hello, " & name & "!"
greetings &= "!!"    # the usual shortcut for: greetings = greetings & "!!"
```

### String as array

A string is an array of characters, and you can access each character with its (0-based) index:
```nim
var letters = "ABCD"
echo letter[0], letter[3]     # will print 'AD'

# you can loop all the letters:
for letter in letters:
  echo " - ", letter
```
