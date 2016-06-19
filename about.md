---
layout: page
title: About Orange 
permalink: /about/
---

Orange is an open source systems programming language made to be highly productive, efficient, and suitible for low-level development through inline assembly and pointers and high-level development through a powerful but simple event system.

Orange has the following goals:

- High productivity through simple syntax 
- Allow for direct memory access with C-style pointers 
- Inline assembly for low-level code (`$mov rax, 5`)
- Be suitable for high- or low-level development (even embedded!) 
- Provide an event system via a [`when` keyword](https://github.com/orange-lang/orange/issues/15)
- Change default attributes (`final`, `virtual`, `protected`, etc.) per project or per file
- Easily bind to existing libraries 
- Quickly access generic functions from libraries as needed (i.e., don't parse a whole header file like C++)

## Safety and Choice 

That last point is pretty interesting; what does that mean? Well, for example, you 
may have noticed that direct memory access is on the list, which is unsafe. If you wanted 
to write more safe code in C++, you'll have to start wrapping your types in `std::unique_ptr`
and the like, and oh boy...

That's just a huge pain. Orange will allow you to change various settings per project to allow these 
things to naturally be a part of the language. You won't have to think any harder to make your 
code as safe as you want it to be. Ownership will transfer as soon as you assign it to a new variable. 
Want to mix and match safe/unsafe code? Just add the `unsafe` attribute when declaring something. 
