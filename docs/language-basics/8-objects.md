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

Objects are data structures, and they do not include methods that in nim are simply procedures having the object as first argument.
Here we will introduce a _FastqRecord_ object having three public attributes (strings) and a tailLen integer.

```nim
# We introduce a FastqRecord type
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
