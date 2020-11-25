---
layout: default
title: Installing Nim
nav_order: 2
---

# Installing Nim
{: .no_toc }

Nim is rapidly evolving and it can be useful to have the possibility to manage multiple
versions of the compiler.
The _nimchoose_ package allows this, and it's my
recommended way of getting _nim_ up and running.

{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Linux

A tool called **choosenim** is my recommended choice:
is not only an easy way to install nim, but also a tool to manage multiple installations
(which can be useful in the future, if you'll start developing serious projects :).
Since most bioinformatics is supported by the **Miniconda package manager**, I also mention that installation as a reasonable way of getting an updated version.

:warning: Installing from repositories (like `apt install nim`)
is a bad idea as system repositories are providing old versions of packages,
and _nim_ is a young and relatively immature programming language:
you need to stick to recent versions to survive.
To make an example at the time of writing (August 2020),
I'm using nim 1.2.6 but my Ubuntu server offers me _nim 0.12_.

### Installation using choosenim

The repository of choosenim ([https://github.com/dom96/choosenim](https://github.com/dom96/choosenim))
contains detailed instructions to install nim on most operating systems.
Here I summarise how to do so on Linux.

#### Prerequisites
Nim relies on a **C compiler** (gcc or clang), that should be installed in most cases
(you can try with `gcc --version` or `clang --version`).
OpenSSL 1.0.2 or newer is also required (the version can be checked with `openssl version`).

If you use Ubuntu and you don't have a compiler you can install the required tools with:

```bash
sudo apt install build-essential openssl zlib1g-dev wget curl
```

#### Installation
To download [choosenim](https://github.com/dom96/choosenim#readme):

```bash
curl https://nim-lang.org/choosenim/init.sh -sSf | sh
```

The installation process will ask you if you want to send anonymous information
to the developers (answer y or n), and finally you should add the nim directory to
[your $PATH](https://opensource.com/article/17/6/set-path-linux)
and then reload the configuration file:

```bash
echo 'export PATH=~/.nimble/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

Did everything work? Try typing `nim` and check that you are getting the splash screen!

### Installation using Miniconda

If you already use Miniconda, the installation is as easy as:

```bash
conda install -y  -c conda-forge nim
```

## macOS

The installation is exactly as in Linux, just remember to install **XCode** from the App Store first,
and then from the command line run this command:
```bash
xcode-select --install
```

to install the compiler (clang) and command line tools, then you can use either
**nimchoose** (recommended) or **conda**, as described above.
