---
layout: default
title: Objects
parent: Language basics
nav_order: 9
---

# Objects
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Objects are data structures, and they do not include methods that in nim are
simply procedures having the object as first argument.
Here we will introduce a _FastqRecord_ object having three public attributes
(strings) and a tailLen integer.

```nim
# We introduce a FastqRecord type. The "*" means its a public type (or attribute),
# and it's useful when we code shared libraries, otherwise can be omitted.

type
  FastqRecord* = object
    name*, seq*, qual*: string
    tailLen: int

# Add a tail of A (default size: 20)
# We will see the 'repeat' function to avoid the loop ;)
proc polyA*(a: var FastqRecord, tailSize = 20) =
  var c = 0;
  while c < tailSize:
    a.seq &= 'A'
    a.tailLen += 1
    c += 1

proc tailTooLong*(a: FastqRecord): bool =
  result = a.tailLen > 30

var seq1: FastqRecord

seq1 = FastqRecord(name : "seq1",
              seq : "CAGATA")

let seq2 = FastqRecord(name : "seq2",
                 seq : "GATTACA")

# Print sequence and tail length, and if tail is too long!
echo seq1.seq, " (", seq1.tailLen, ") ", seq1.tailTooLong()

# Add tail (default len)
# object.procedure() will pass the object as first parameter
seq1.polyA()
echo seq1.seq, " (", seq1.tailLen, ") ",  seq1.tailTooLong()

# Add tail (custom len)
seq1.polyA(18)
echo seq1.seq, " (", seq1.tailLen, ") ", seq1.tailTooLong()
```


## Object vs Object Ref

Similar sintax and sometimes confusing. An `object` cannot be modified by
procedures (functions), but a `Ref object` can.

### Definining the types
The definition is identical, except for the `ref`, of course:
```nim
type
  bedRegion = object
    start, end: int
    chr, description: string

type
  bedInterval = ref object
  start, end: int
  chr, description: string
```
### Calling a function

When calling a procedure, the first argument can be passed explicitly or with
the object notation, using the dot:

```nim
proc say(name: string) =
  echo "Hello ", name

let name = "Andrea"

# The following are identical:
say(name)
name.say()
```
### A full example

The following example compares two similar types, one declared as _object_,
and the other as _object ref_, showing how the procedure can or cannot
modify the calling object.

{% gist eb72a4b1f3cf09a087bf46a11f415226 %}
