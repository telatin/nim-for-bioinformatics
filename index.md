---
layout: default
title: Home
nav_order: 1
description: "Nim for Bioinformatics"
permalink: /
---

# Nim for Bioinformatics
{: .fs-9 }

Nim is a compiled language with a Python-like syntax.
Fast and easy to share binaries, an easy to learn language.

{: .fs-6 .fw-300 }

[Start reading](#what-is-nim){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Script on GitHub](https://github.com/telatin/nim-stuff){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What is Nim?

From the [website](https://nim-lang.org):

>Efficient, expressive, elegant – Nim is a statically typed compiled systems programming language. It combines successful concepts from mature languages like Python, Ada and Modula.

A different way of seeing this is: _Nim is a compiled language that can be as fast as C, with a syntax that can be as intuitive as Python_.

### Interesting features

- It's a **compiled language** that can produce fast programs
  - Sometimes it will be really **convenient to distribute** a binary rather than a script that will rely on several dependencies
- The syntax is Python-like and will look familiar for a lot of bioinformaticians
- It already has a niche in web applications (with a framework called Jester)
  - It can be compiled to javascript, so you can have backend and frontend homogeneously coded
- Good support of metaprogramming, that allows to create domain specific languages
- **C libraries** can be easily wrapped and utilized in Nim programs

There are links to bioinformatics projects in Nim in a [separate page](bibliography).

## How does this book work?

This document aims at being a gentle but concise introduction to nim for bioinformaticians. The assumptions are:
- You already are very familiar with Linux and the command line (macOS terminal is equally supported)
- You have some scripting  knowledge. Knowing some Python is a very good way of starting your journey to Nim, but any other programming language can do the trick
- You know bioinformatic file formats and are familiar with Next Generation Sequencing (that happens to require a lot of high throughput processing of quasi-garbage files)

There are [excellent tutorials](resources), so this book focuses on complete minimal examples for each topic presented.

## Can Nim be my first programming language?

While it's feasible to learn Nim without an extensive knowledge of programming, if you never wrote any kind of program or script I would recommend to start with something different. A good choice for most of the bioinformatics needs is Python.
If you get stuck you are more likely to find a solution to your problem if you adopt a popular programming language (like Python or Perl), and if you need to perform some common tasks (like parsing a GenBank file) you will find robust libraries for Perl and Python, but you are un likely to find a heavily tested and adopted solution for Nim, at the moment.
I think Nim has concrete possibilities to catch up quickly (for example, it's relatively straighforward to "adapt" C/C++ libraries to be used from Nim).
It's also worth remembering that nowaday you probably don't need to program yourself, as there is plenty of bioinformatics packages addressing a wide variety of needs.
