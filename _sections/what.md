---
index: 1
---

# What?

Orange is a statically typed, multi-paradigm (imperative, object-oriented,
reflective) systems programming language with focus on high productivity,
features for DRY code, and a smooth syntax without sacrificing efficiency.

Orange will give control to the user for memory management, with access to
raw pointers and a non-tracing garbage collection that can be disabled.

Orange is targeting high-level development on OS X, Linux, and Windows, as
well as support for low-level development such as kernels and embedded
programming.  

It is currently in the alpha phase, and language features are getting tweaked
constantly, so subscribe to our
[RSS feed]({{ "/feed.xml" | prepend: site.baseurl }}) for updates.

	extern printf(char *s, ...) -> int32

	for (var i = 0; i < 10; i++)
		printf("Hello, world %d!\n", i)
	end
