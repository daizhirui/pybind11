![pybind11 logo](https://github.com/wjakob/pybind11/raw/master/logo.png)

# pybind11 — Seamless operability between C++11 and Python

[![Documentation Status](https://readthedocs.org/projects/pybind11/badge/?version=latest)](http://pybind11.readthedocs.org/en/latest/?badge=latest)
[![Build Status](https://travis-ci.org/wjakob/pybind11.svg?branch=master)](https://travis-ci.org/wjakob/pybind11)
[![Build status](https://ci.appveyor.com/api/projects/status/rfbxqkgxkcrxdu0f?svg=true)](https://ci.appveyor.com/project/wjakob/pybind11)

**pybind11** is a lightweight header-only library that exposes C++ types in Python
and vice versa, mainly to create Python bindings of existing C++ code. Its
goals and syntax are similar to the excellent
[Boost.Python](http://www.boost.org/doc/libs/1_58_0/libs/python/doc/) library
by David Abrahams: to minimize boilerplate code in traditional extension
modules by inferring type information using compile-time introspection.

The main issue with Boost.Python—and the reason for creating such a similar
project—is Boost. Boost is an enormously large and complex suite of utility
libraries that works with almost every C++ compiler in existence. This
compatibility has its cost: arcane template tricks and workarounds are
necessary to support the oldest and buggiest of compiler specimens. Now that
C++11-compatible compilers are widely available, this heavy machinery has
become an excessively large and unnecessary dependency.

Think of this library as a tiny self-contained version of Boost.Python with
everything stripped away that isn't relevant for binding generation. The core
header files only require ~2K lines of code and depend on Python (2.7 or 3.x)
and the C++ standard library. This compact implementation was possible thanks
to some of the new C++11 language features (tuples, lambda functions and
variadic templates). Since its creation, this library has grown beyond
Boost.Python in many ways, leading to dramatically simpler binding code in many
common situations.

Tutorial and reference documentation is provided at
[http://pybind11.readthedocs.org/en/latest](http://pybind11.readthedocs.org/en/latest).

## Core features
pybind11 can map the following core C++ features to Python

- Functions accepting and returning custom data structures per value, reference, or pointer
- Instance methods and static methods
- Overloaded functions
- Instance attributes and static attributes
- Exceptions
- Enumerations
- Callbacks
- Custom operators
- STL data structures
- Smart pointers with reference counting like `std::shared_ptr`
- Internal references with correct reference counting
- C++ classes with virtual (and pure virtual) methods can be extended in Python

## Goodies
In addition to the core functionality, pybind11 provides some extra goodies:

- pybind11 uses C++11 move constructors and move assignment operators whenever
  possible to efficiently transfer custom data types.

- It is possible to bind C++11 lambda functions with captured variables. The
  lambda capture data is stored inside the resulting Python function object.

- It's easy to expose the internal storage of custom data types through
  Pythons' buffer protocols. This is handy e.g. for fast conversion between
  C++ matrix classes like Eigen and NumPy without expensive copy operations.

- pybind11 can automatically vectorize functions so that they are transparently
  applied to all entries of one or more NumPy array arguments.

- Python's slice-based access and assignment operations can be supported with
  just a few lines of code.

- Everything is contained in just a few header files; there is no need to link
  against any additional libraries.

### License

pybind11 is provided under a BSD-style license that can be found in the
``LICENSE.txt`` file. By using, distributing, or contributing to this project,
you agree to the terms and conditions of this license.
