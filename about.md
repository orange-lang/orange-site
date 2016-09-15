---
layout: page
title: About Orange
permalink: /about/
---

Orange is an open source systems programming language made to be productive, efficient, and extendible. It's compiled, statically typed, and supports OOP or imperative programming. Also, functions are first-class citizens!

Orange has the following goals:

- Be Productive. Provide a simple syntax for writing code quickly and make it easy to download and install project dependencies. Provide strict type checking to make sure basic type errors can't happen.
- Be Extendible. Allow developers to extend new interfaces to existing types, and allow for creating/downloading compiler extensions that can add new language features and code checks.
- Be Flexible. Combine the extendibility and productivity to make Orange suitable for any kind of development, from embedded programming to high-level applications like web servers.

## Safety and Choice

The core language of Orange is memory unsafe. This is by choice; for low-level applications, memory should be managed by hand.

But that's not the way all code should work. Through language extensions, users could download a garbage collection extension, or a automatic reference counting extension - none of these need to be developed by Orange, and any could be used to fit the project's needs. It should be easy to set up project with default sets of extensions, like if there was a "Hello World" starter kit of extensions that a new project would use.

The choice that Orange enables forces an extra step on examining statically typed, compiled code: when looking at a new project, your first stop would be the project definition. In the project definition, you'd be able to see what extensions they are using so you can insert yourself into the appropriate mindset. It's not radically different than from when Apple first introduced ARC to Objective-C, or if you're working on a javascript project that transpiles the code.
