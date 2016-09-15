---
layout: post
title:  "Still alive!"
date:   2016-09-14 23:24:50
categories: blog
---

It's been a long year, and I've been [busy](https://github.com/orange-lang/orange/tree/rev-2) trying to refine what Orange is. Every few weeks or so I'll take a step back from working on Orange to work on something else. It helps to give me perspective on what I want out of a language, since I've never used a language that I've found "perfect."

I've created a very long list of things I want, but here are the highlights:

- Statically typed
- Compiled to machine code so embedding on tiny platforms isn't out of the question
- Allow for generic programming.
- Type annotations should only be required if they can't be inferred (note: not exactly Haskell's level of type inferrence, but something)
- Syntax that's simple and not too terse (looking at you, C++)
- Package manager support
- Support for multiple paradigms (specifically, imperative and OOP)
- Functions should be first-class citizens.
- Modular support to hook into the compiler phases.

# Extendible Compiler

That last point is what has been interesting me the most lately. I want Orange to provide a base language: a language that is suitable for systems programming. But just like programmers download libraries to make developing new applications easier, I don't think it's unreasonable for programmers to have the ability to download tools to make writing _code_ easier for their situation.

For example, not all projects need manual memory management, so what if there was an automatic-reference-counting extension? Or what if somebody wanted to create a smaller language for writing tests? You could create a DSL that parses to the Orange's AST. What if you wanted extra verification to happen on your code, like checking for race conditions or use-after-free errors?

All of these things could monolithically be added to the compiler itself, but that would limit _choice_. The open source community should be able to develop libraries and extensions as they see fit and not have to worry about them ever getting merged into the main Orange repository.

This does add an extra layer of complexity when looking at a new Orange project: the first stop would be the project definition. What extensions are they using? This should be as transparant as possible so nobody is taken aback from extra features in the code.

# A Final Revision

I wrote a [second revision](http://docs.orange-lang.org/v/rev-2/) to the Orange documentation a while ago, but I'm still not happy with it. I'm currently working on one final revision, which is slightly more inspired from the capabilities of Haskell.

The final major revision will see a few things changed:

- Introduction of a `Number` interface and a larger reliance on interfaces to define operations on types.
- Simplification on how Generics are defined and used
- Strict type checks. Numbers of different types (int and float) won't be casted implicitly.
- Strict type aliasing.
	- String is an alias for `Char[]`, which are interchangeable.
	- You could define a strict alias of `Year` to `Int`, which are not interchangeable.
- Stronger focus on functions as a first-class citizen.

The `Number` interface defines the basic mathematical binary operations, and it's implemented for builtin types. New types could implement this interface, and it can even be implemnted for existing types (see [Type Extensions](http://docs.orange-lang.org/v/rev-2/language/extensions.html)).

The focus on interfaces is inspired by how Go and Rust handle methods, but make no mistake, Orange will still have classes; they will simply be treated as a simultaneous definition of a struct and an interface that are tied together.

# Work in Progress

As always, Orange is a work in progress! It's come a long way from its first, aimless commit in 2014. I've put more time lately into figuring out what Orange should be instead of commiting the first thing that comes into mind. In my opinion, it's shaping up to be a fantastic language that I can't wait to use for my own projects.

# Discuss

Orange is on [Gitter](https://gitter.im/orange-lang/orange) now! The [Google Group](https://groups.google.com/forum/?fromgroups#!forum/orange-lang) still exists for long-form conversations, as well. Feel free to discuss Orange or even throw some ideas at me!
