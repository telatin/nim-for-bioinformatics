---
layout: default
title: Tuples
parent: Language basics
nav_order: 7
---

# Tuples
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Tuples

Arrays and sequences are homogeneous lists, while tuples can store a fixed-size  **list of hetherogeneous variables**.

```nim
let mixedItems = ("Nim", 42, 0.33)
echo mixedItems[1]                    # will print 42
```

What makes tuples very nice to use, is that you can name each item:

```nim
var
  ctgStats: tuple[name: string, size: int, coverage: float]
  thisCtgStats = (name: "Contig1", size: 1400, coverage: 12.44)

# Access items and edit them:
echo thisCtgStats.name, " size is ", thisCtgStats.size, " bp."
thisCtgStats.name = "Contig_1"
```

### An example

Here we use a tuple to create a custom _type_ (ctgInfo) to store three properties
of an assembled contig (the name, the coverage and its length)
```nim
# new type that is a tuple
type
    ctgInfo = tuple[name: string, cov: float, length: int]

# You can create a sequence of type 'ctgInfo'
var
  contigs = newSeq[ctgInfo]()

# Create some instances and make a sequence
var
    p1: ctgInfo = (name: "p1", cov: 60.0, length: 10)
    p2: ctgInfo = (name: "p2", cov: 20.0, length: 10)
    p3: ctgInfo = (name: "p3", cov: 30.0, length: 10)
    p4: ctgInfo = (name: "p4", cov: 30.0, length: 10)
    assembly = @[p1,p2,p4,p3]

# Or add tuples to the Sequences sequence
contigs.add((name: "p24", cov: 2990.0, length: 10))
contigs.add((name: "p41", cov: 30.0, length: 10))
contigs.add((name: "p94", cov: 300.0, length: 210))

# Print the sequence
echo "Contigs: ", assembly

# Loop the sequence
for ctg in assembly:
  echo ctg.name, "\t", ctg.cov, "X", "\tlen=", ctg.length, " bp"
```

The output will be:
```text
Contigs sequence: @[(name: "p1", cov: 60.0, length: 10), (name: "p2", cov: 20.0, length: 10), (name: "p4", cov: 30.0, length: 10), (name: "p3", cov: 30.0, length: 10)]
p1  60.0X   len=10 bp
p2  20.0X   len=10 bp
p4  30.0X   len=10 bp
p3  30.0X   len=10 bp
```
