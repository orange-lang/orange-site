---
layout: post
title:  "Hello, world!"
date:   2015-07-06 18:32:57
categories: blog
---

	extern printf(char *s, ...) -> int32 
	printf("Hello, world!\n")

Orange is a new language that's still in heavy development. As you can see from the example above, 
you have to link against C functions right now to create any "real" code.

## Present Orange

Let's look at a more complicated example than our hello world:

	extern printf(char* s, ...) -> int32

	# increment all elements in an array by 1 
	# arr: the array to increment 
	# sz: the size of the array
	def inc(var arr, var sz) 
		arr[i]++ for (var i = 0; i < sz; i++)
	end 

	# declare variables with var
	var arr = [5, 3, 2, 3, 6]

	# ... or with literal types!
	int arr_sz = sizeof(arr)/sizeof(int) 

	inc(arr, arr_sz) 

	for (var i = 0; i < arr_sz; i++) 
		printf("%d\n", arr[i])
	end 

You may be able to tell that's it's very C-like, in some ways: arrays are just pointers, so 
they're pass-by-reference, and `sizeof` exists for you to get the size of data primitives. 

You may wonder what's the significance of `var` in the function header of `inc`. Well, if 
a function has a parameter whose type is `var`, then that parameter is a generic, and so is 
the function. With generics, a unique function is created for each of the parameters that's 
passed in. 

Orange didn't always look this way, however. A few weeks ago, this would've been the syntax:

	extern printf(char* s, ...) -> int32 

	def inc(arr, sz)
		arr[i]++ for (i = 0; i < sz; i++)
	end

	arr = [5, 3, 2, 3, 6]
	arr_sz = sizeof(arr)/sizeof(int)

	inc(arr, arr_sz)

In terms of typing, it is indeed more simple, but it allowed for a lot of errors, since if 
you reassign a value to a variable and mistype its name, it would just create a new variable. 
Try tracking that one down!

## Future of Orange 

Orange has come quite a ways since its inception in December 2014. It's nowhere near a 1.0 release, 
but it's shaping up to be one hell of a langauge. It does bring up the question about how the 
high-level features will work. 

Here's an example of what's in the pipeline for something like concurrency:

	class SomeClass 
		int num = 0
	end 

	def randomizeNum(var myObj, var times)
		for (var i in [0..times])
			# no need for -> in Orange 
			myObj.num = Math.rand()

			sleep(1)

			# Send it to a channel, if one is registered 
			# channels are buffered: writing is non-blocking 
			send myObj.num
		end 
	end

	var myObj = new SomeClass
	var times = 20 

	# call randomizeNum concurrently 
	# write results to channel named chan 
	do randomizeNum(myObj, times) -> chan 

	# let's only get half of our random numbers
	for (var i in [0..times/2]) 
		# get a number from chan, waiting until 
		# one is available 
		var num <- chan 
		print("Random number: #{num}")
	end 

	# chans are aware of threads; wait for 
	# randomizeNum to finish
	wait chan 