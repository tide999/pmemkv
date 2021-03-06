# pmemkv

[![Travis build status](https://travis-ci.org/pmem/pmemkv.svg?branch=master)](https://travis-ci.org/pmem/pmemkv)
[![GHA build status](https://github.com/pmem/pmemkv/workflows/pmemkv/badge.svg?branch=master)](https://github.com/pmem/pmemkv/actions)
[![Coverity Scan Build Status](https://scan.coverity.com/projects/18408/badge.svg)](https://scan.coverity.com/projects/pmem-pmemkv)
[![Coverage Status](https://codecov.io/github/pmem/pmemkv/coverage.svg?branch=master)](https://codecov.io/gh/pmem/pmemkv/branch/master)
[![PMEMKV version](https://img.shields.io/github/tag/pmem/pmemkv.svg)](https://github.com/pmem/pmemkv/releases/latest)
[![Packaging status](https://repology.org/badge/tiny-repos/pmemkv.svg)](https://repology.org/project/pmemkv/versions)

Key/Value Datastore for Persistent Memory

## Overview

`pmemkv` is a local/embedded key-value datastore optimized for persistent memory.
Rather than being tied to a single language or backing implementation, `pmemkv`
provides different options for language bindings and storage engines.

For more information, including **C API** documentation in form of manuals,
and **C++ API** docs in form of Doxygen html files see: https://pmem.io/pmemkv.
Documentation is available for every branch/release. For most recent always see (**master** branch):
 * [C++ docs](https://pmem.io/pmemkv/master/doxygen/index.html),
 * and [C manpage libpmemkv(3)](https://pmem.io/pmemkv/master/manpages/libpmemkv.3.html).

Latest releases can be found on the ["releases" tab](https://github.com/pmem/pmemkv/releases).

Up-to-date, current support/maintenance status of branches/releases is available on
[pmem.io](https://pmem.io/pmemkv/index.html#releases-support-status).

There is also a small helper library `pmemkv_json_config` provided.
See its [manual](doc/libpmemkv_json_config.3.md) for details.

### README's table of contents:
- [Installation](#installation)
- [Language Bindings](#language-bindings)
- [Storage Engines](#storage-engines)
- [Tools and Utilities](#tools-and-utilities)

## Installation

[Installation guide](INSTALLING.md)
provides detailed instructions how to build and install `pmemkv` from sources,
build rpm and deb packages and explains usage of experimental engines and pool sets.

- [Building from Sources](INSTALLING.md#building-from-sources)
- [Installing on Fedora](INSTALLING.md#installing-on-fedora)
- [Installing on Ubuntu](INSTALLING.md#installing-on-ubuntu)
- [Using Experimental Engines](INSTALLING.md#using-experimental-engines)
- [Building Packages](INSTALLING.md#building-packages)
- [Using a Pool Set](INSTALLING.md#using-a-pool-set)

## Language Bindings

`pmemkv` is written in C/C++ and it is used by bindings for Java, Node.js,
Python, and Ruby applications.

![pmemkv-bindings](https://user-images.githubusercontent.com/12031346/65962933-ff6bfc00-e459-11e9-9552-d6326e9c0684.png)

### C/C++ Examples

Examples for C and C++ can be found within this repository in [examples directory](./examples/).

### Other Languages

Abovementioned bindings are maintained in separate GitHub repositories, but are still kept
in sync with the main `pmemkv` distribution.

* Java - https://github.com/pmem/pmemkv-java
* Node.js - https://github.com/pmem/pmemkv-nodejs
* Python - https://github.com/pmem/pmemkv-python
* Ruby - https://github.com/pmem/pmemkv-ruby

## Storage Engines

`pmemkv` provides multiple storage engines that conform to the same common API, so every engine can be used with
all language bindings and utilities. Engines are loaded by name at runtime.

| Engine Name  | Description | Experimental? | Concurrent? | Sorted? |
| ------------ | ----------- | ------------- | ----------- | ------- |
| [blackhole](doc/libpmemkv.7.md#blackhole) | Accepts everything, returns nothing | No | Yes | No |
| [cmap](doc/libpmemkv.7.md#cmap) | Concurrent hash map | No | Yes | No |
| [vsmap](doc/libpmemkv.7.md#vsmap) | Volatile sorted hash map | No | No | Yes |
| [vcmap](doc/libpmemkv.7.md#vcmap) | Volatile concurrent hash map | No | Yes | No |
| [csmap](doc/ENGINES-experimental.md#csmap) | [Concurrent sorted map](https://pmem.io/libpmemobj-cpp/master/doxygen/classpmem_1_1obj_1_1experimental_1_1concurrent__map.html) | Yes | Yes | Yes |
| [radix](doc/ENGINES-experimental.md#radix) | [Radix tree](https://pmem.io/libpmemobj-cpp/master/doxygen/classpmem_1_1obj_1_1experimental_1_1radix__tree.html) | Yes | No | Yes |
| [tree3](doc/ENGINES-experimental.md#tree3) | Persistent B+ tree | Yes | No | No |
| [stree](doc/ENGINES-experimental.md#stree) | Sorted persistent B+ tree | Yes | No | Yes |

The production quality engines are described in the [libpmemkv(7)](doc/libpmemkv.7.md#engines) manual
and the experimental engines are described in the [ENGINES-experimental.md](doc/ENGINES-experimental.md) file.

[Contributing a new engine](CONTRIBUTING.md#creating-new-engines) is easy and encouraged!

## Tools and Utilities

Benchmarks' scripts and other helpful utilities are available here:

https://github.com/pmem/pmemkv-tools
