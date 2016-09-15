---
index: 1
---

# What?

Orange is a statically typed, multi-paradigm (imperative, object-oriented) systems programming language with a focus on high productivity and extendability.

Orange doesn't have a garbage collector, reference counting, or smart pointers - by default, it's an unsafe language. But the Orange compiler is extendable, and so users are free to mix and choose any compiler extensions to shift the language to include features that may be suitable for their project - like object lifetime checks, garbage collection, or adding a DSL to write beautiful unit tests.

Compiler extensions aren't macros - these are actual hooks into the various compiler phases that can either be extended or replaced entirely. Orange is _modular_.

Orange is targeting high-level development on OS X, Linux, and Windows, as
well as support for low-level development such as kernels and embedded
programming.

It's currently in the alpha phase, and language features have been getting tweaked constantly. The focus is narrowing and the final reivision for the language spec is almost finished, so subscribe to our [RSS feed]({{ "/feed.xml" | prepend: site.baseurl }}) for updates.
