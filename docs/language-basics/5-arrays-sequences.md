---
layout: default
title: Arrays and Sequences
parent: Language basics
nav_order: 6
---

# Arrays and Sequences

Arrays and sequences are data structure containing a series of variables. The former are similar to C arrays (and are usually needed when efficiency is a priority), while sequences are more similar to Python lists (and are more flexible at the expence of performances).

{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Arrays

Array sizes are specified at compile-time and cannot be given or changed. An array is defined by two parameters: its size and the type of values it will store.
The following example initialize an empty array of two integers, and it's use to store the number and the total size of sequences.
Each item is accessed with a 0-based index:

```nim
var
 count_and_sum: array[2, int]

count_and_sum[0] = 20
count_and_sum[1] = 200

echo "# sequences: ", count_and_sum[0], "; total size: ", count_and_sum[1]
echo count_and_sum
```

Its nature of fixed size lists makes them of limited use for beginners, but they can be of immense use while optimizing your programs.

## Sequences

Sequences are variable-length lists. They can be initialized with the elements or as empty lists:

```nim
var
  StopCodons = @["UAG", "UAA", "UGA"]   # Inferred as seq of strings
  SequencePatterns: seq [string]        # empty as seq of strings
  Codons  = newSeq[string](64)          # seq of strings, 64 slots
  numbers = newSeq[int]()               # empty sequences of ints
```

### Adding and removing items

The add and delete methods will intuitively work on sequences as follows:

```nim
#Adding
sequences.add("ATAGG")
# Removing by index
sequences.delete(0)
```

## Accessing items
Each item can be accessed by index, as it happens with the arrays. The total number of items is returned by the len function.

```nim
let firstItem = sequences[0]     # zero based positive indexes
let lastItem  = sequence[^1]     # this to start from the end

# Slicing
echo sequences[0 .. 3]
echo sequences[0 ..< 3]

echo "Total sequences: ", len(sequences)
```

## Looping through items and indexes

A for loop can be used to capture both index and value of each element:

```nim
#Looping through indexes and values
for index, value in sequences:
  echo ">Seq_", index, "\n", value
```

## A script using Sequences

The idea of this guide is to provide simple examples, and this shows different declarations, how to add and loop through a sequence.

:information: Note that the `echo` command will add a newline at the end of the string.
Here we will use the `stdout.writeLine` command instead.

```nim
var
  sequences : seq[string]
  Bases = @['A', 'C', 'G', 'T'] # seq of chars
  Codons = newSeq[string](64)   # seq of strings, 64 slots
  i = 0 # This will be used as counter later

# Add some sequences
sequences.add("GAGGA")
sequences.add("GCAA")
sequences.add("GAGGATT")

let firstItem = sequences[0]
echo "Total sequences: ", len(sequences), " the first is ", firstItem

#Looping through indexes and values
for index, value in sequences:
  echo ">Seq_", index, "\n", value

# Codons: populating the sequence
echo "The empty Codons array has size: ", len(Codons)


for first in Bases:
  for second in Bases:
    for third in Bases:
      Codons[i] = first & second & third
      stdout.write Codons[i]
      i += 1
      # Adding a newline every 8 codons (space otherwise)
      if i mod 8 != 0:
        stdout.write " "
      else:
        stdout.write "\n"
```

This script above will produce the following output:

```text
Total sequences: 3 the first is GAGGA
>Seq_0
GAGGA
>Seq_1
GCAA
>Seq_2
GAGGATT
The empty Codons array has size: 64
AAA AAC AAG AAT ACA ACC ACG ACT
AGA AGC AGG AGT ATA ATC ATG ATT
CAA CAC CAG CAT CCA CCC CCG CCT
CGA CGC CGG CGT CTA CTC CTG CTT
GAA GAC GAG GAT GCA GCC GCG GCT
GGA GGC GGG GGT GTA GTC GTG GTT
TAA TAC TAG TAT TCA TCC TCG TCT
TGA TGC TGG TGT TTA TTC TTG TTT
```
