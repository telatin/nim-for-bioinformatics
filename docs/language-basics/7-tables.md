---
layout: default
title: Tables
parent: Language basics
nav_order: 8
---

# Tables
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Tables are sequences of pairs, and they are similar to what other languages call hashes, associative arrays or dictionaries, but they require a library to be imported to be used (tables).

:information: In my opinion, tables are less needed in nim if compared with other languages, as a custom type will probably prove to be a good alternative. See next chapter.

Nim tables are typed, but keys and values can have a different type. As usual let's see how to declare an empty table and how to initialize a table with an assignment:

```nim
# You need to import the 'tables' library first
import tables

# create a new Table with and without data assignment
var
  cuttingPosition : initTable[string, int]()
  motifs = {"EcoRI": "GAATTC", "HindIII": "AAGCTT"}.toTable  

# Add a key/value pair:
motifs["HpaI"] = "GTTAAC"
cuttingPosition["HpaI"] = 3
```

### Ordered tables
A table will not keep its item ordered (unlike arrays and sequences), but if for some reasons the insertion order matters, ordered tables are the solution. Instead of using `Table[A, B]` type, you will use the `OrderedTable[A, B]` type.

### Count tables
A CountTable initialise a counter for each key, that can be incremented by 1 or another integer:

```nim
var
  SequenceCounts = initCountTable[string]()

# to increase of 1
SequenceCounts.inc("GATTACA")

# to increase of 10
SequenceCounts.inc("TATA", 10)
```
