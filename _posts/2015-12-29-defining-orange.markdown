---
layout: post
title:  "Defining Orange"
date:   2015-12-29
categories: blog
---

After completing a
[second full rewrite](https://github.com/orange-lang/orange/pull/21) of the
compiler, defining what kind of language Orange will be has still been a
struggle.

Currently, Orange sits around 20K lines of code: a mix between C++ and tests
written in Orange itself. Working with a decent chunk of C++ code for Orange
and C# at work has continued to
[inspire](https://github.com/orange-lang/orange/issues/24)
[me](https://github.com/orange-lang/orange/issues/15) as to what kind of
workflow I'd like to see possible with the language.

There are a few features that I'm considering a must for Orange:
	- Optional non-tracing garbage collection
	- Object Orientation
	- Reflection
	- Package Management and other Utilities

# Optional non-tracing garbage collection

C++'s `std::shared_ptr<T>` approach to a reference-counting garbage collection
system is handy, but a giant pain to use. Orange's garbage collection
will work more similarly to Apple's
[Automatic Reference Counting](https://en.wikipedia.org/wiki/Automatic_Reference_Counting).

If possible, Orange will automatically insert code to release objects at
compile-time to avoid unnecessary run-time checks of reference counts.

Orange will still allow this feature to be disabled, being replaced with manual
`delete` calls when manually managing memory is important.

# Object Orientation

Support for classes is currently being developed in my
[personal fork](https://github.com/rfratto/orange/tree/classes) of Orange, and
is on its way in.

Orange _is_ multi-paradigm so imperative programming can
still be used above OOP, but similarly to C++, giving the choice is important.

# Reflection

The necessity of reflection is a hot topic amongst programmers, but I believe
that it can be an extremely useful tool for certain systems like unit tests
or other dynamic environments. Support for reflection will
be built into the runtime type information of Orange, and can be disabled,
similarly to gcc/clang's `-fno-rrti` flag.

# Package Management and other Utilities

As (currently) the sole maintainer of Orange, I can't reasonably include
everything into the standard library on my own. C++, after 30 years, still
doesn't have package management. Any modern programming language should have
package management built in.

Orange will support globally installing packages and installing packages
locally to a project, where the project definition file (`orange.settings.json`)
will define the dependencies of the language. It should be able to grab
dependencies straight from Github or a package directory service.

Just being able to call `orange install mylibrary` isn't enough for a compiler
command line interface: other tools, such as code formatters, project creation,
code-completion interfaces, package uploading, and testing should be built into
the binary, and so it will.  

# Defining Orange

Orange is a portable, compiled, statically typed, multi-paradigm (imperative,
object-oriented, reflective) systems programming language with focus on high
productivity, features for DRY code, and a smooth syntax without sacrificing
efficiency.

# Discuss

Disagree with anything in this post, or have any ideas? Feel free to comment
in the Disqus module below, our IRC channel
[#orange-lang](http://webchat.freenode.net/?channels=%23orange-lang) on
irc.freenode.net, or
[Google Group](https://groups.google.com/forum/?fromgroups#!forum/orange-lang).
