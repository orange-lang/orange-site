---
layout: page
title: Examples
permalink: /examples/
---

_Note: this examples will be out of data soon with the upcoming revision to Orange. See [this post]()http://orange-lang.org/blog/2016/09/14/still-alive.html for more details._

# Hello, World!

    extern printf(char* s, ...) -> int32

    for (var i = 0; i < 10; i++)
      printf("Hello world, %d!\n", i)
    end

# Pointers

    def swap(var a, var b)
      temp = *a
      *a = *b
      *b = temp
    end

    int a = 3, b = 5
    swap(&a, &b)

# Arrays

    extern printf(char* s, ...) -> int32
    var arr = [0, 5, -1, 3, 9, 12]
    var sum = 0

    for (var i = 0; i < sizeof(arr)/sizeof(int); i++)
      sum += arr[i]
    end

    printf("sum: %d\n", sum)

# Classes

    extern printf(char* s, ...) -> int32

    class Person
      public char* name

      public Person(char* name)
        @name = name
      end
    end

    Person john = Person("Johnny")
    printf("Hello, %s!\n", john.name)
