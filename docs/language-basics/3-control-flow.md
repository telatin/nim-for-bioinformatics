---
layout: default
title: Control Flow
parent: Language basics
nav_order: 4
---

# Control flow
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

This page briefly present the syntax for common control-flow patterns.
Some more details can be presented in the worked examples.

## Conditionals
To execute a set of statements if a condition is satistisfied. "If statements" in Nim have the typical Python-like structure as in the following example:

```nim
let firstLine = ">Sequence1"

if firstLine[0] == '>':
  echo "A nice FASTA file!"
elif firstLine[0] == '@':
  echo "A FASTQ record"
else:
  echo "ERROR: unrecognized format :("
```

Interestingly, **if statements** return the value of the expression they evaluate to,
so you can mimicry a ternary operator like this:

```nim
# If MinLen > 0 then assign true, else assign false (to TruncateSeq)
var TuncateSeq = if MinLen > 0: true
               else: false
```

## While

This loop will be execute while a condition is satisfied.
It's used when you do not know in advance when to stop.

```nim
while sumLen < halfGenome:
  let CtgSize = getNextContig()
  sumLen += CtgSize
```

## For
For loops will repeat a set of instructions a defined number of times
(or one time for each element of a set).
For loops are very useful to iterate arrays and sequences,
so more examples will be presented there.

```nim
for i in countup(1, 10):
  echo i, "..."
```

The **countup** function returns a list of integer starting from the first (in the example 1) to the last (in the example 10).
The `..` **iterator** is also commonly used, and it's important to surround it by spaces (including its `..<` variant):

```nim
# This will iterate from 1 to 10 (included)
for i in 1 .. 10:
  echo "inclusive: ", i

# This will iterate from 1 to 9 (included)
for i in 1 ..< 10:
  echo "exclusive: ", i
```
