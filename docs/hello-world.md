---
layout: default
title: Hello World
nav_order: 3
---

# Hello World

If you ever downloaded a source of a program written in C or C++ and compiled it, you'll know that you'll need to compile it before running it.

Nim works in a peculiar way: the `.nim` source files are compiled to C files, that are then compiled in machine code by a common C compiler (gcc or clang).

## Your first Nim program

Let's take a very simple example, that we can save as `hello.nim`:

```python
# This is a comment
echo "Hello, World!"
```

As you can see, this is a very simple script where we wrote a comment line (anything after a #) and an instruction to print a string. The standard library is available by default and doesn't need to be imported, and you don't need to create a "main" procedure, unless you want to.

Here you see that the familiar print command becomes echo, that works like Python trying to convert to string all arguments that it receives. In nim strings are surrounded by double quotes (not single).

To compile it, the command is `nim c` or `nim compile`:
```bash
nim c hello.nim
```

This will produce:

```text
Hint: used config file '/Users/telatina/miniconda3/nim/config/nim.cfg' [Conf]
Hint: system [Processing]
Hint: widestrs [Processing]
Hint: io [Processing]
Hint: hello [Processing]
CC: stdlib_io.nim
CC: stdlib_system.nim
CC: hello.nim
Hint:  [Link]
Hint: 14213 LOC; 1.717 sec; 16.102MiB peakmem; Debug build; proj: /Users/telatina/hello.nim; out: /Users/telatina/hello [SuccessX]
```

this will produce a file called **hello** in the same director. This is the **program's binary**, and you can run it by:
```
./hello
```

To obtain, as expected, this output:
```
Hello, World
```

#### Compile and execute
If you want to compile and execute the compiled program immediately, you can add the `-r` (run) switch.
```
nim c -r hello.nim
```

## Your first syntax error

Since the time will arrive to experience some sort of error during the compilation, let's break the ice. Copy your hello.nim to wrong.nim and replace the double quotes with single quotes, then compile the new program:
```
echo 'Hello, World!'
```

If you compile you'll receive an error.
Nim will tell you the line and column when this happened (line 1, column 8) and
a (usually) clear message: _missing closing ' for character literal_.
```
/Users/telatina/hello.nim(1, 8) Error: missing closing ' for character literal
```

In this case the problem is that you must use double quotes for strings, while single quote is only for single characters like `echo 'H'`, so the interpreter after finding a single quote and a character (H) was expecting its closing quote.

## Summarising

We tested that nim is properly installed creating a minimal script with a single statement (echo). Then we used the nim compiler to produce a binary file to be executed.

The compilation step required nim to produce a temporary C code, and clang to compile it to machine code.
During the compilation step you'll receive _hints_, _warnings_ and... sometimes _errors_.
If your code will not compile because of errors, those will be _compile time errors_, usually related to a syntax error.
If your program compiles but then refuses to run or crashes after starting... they are _runtime errors_, that can be
harder to debug.

If you want to read more about compiling options, check the [official documentation](https://nim-lang.org/docs/nimc.html).
