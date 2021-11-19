<p align="center">
<h1 align="center">sea</h1>
</p>

<p align="center">
<h3 align="center">A new syntax for C &amp; C++, in one header file</h3>
</p>

<br />

sea is a new syntax for C &amp; C++. It can be used by adding the following line of code to a `.c`, or `.cc`/`.cpp` file:

```cpp
#include <sea.h>
```

> **IMPORTANT NOTE:** After including sea, certain features may be overwritten, such as keywords. For this reason `sea.h` is very easy to modify, and you can remove certain features if you do not want to use them.

<br />

### What is sea, exactly?

As metionned previously, sea is a new syntax for C/C++. Effectively, it uses user-defined macros to provide new keywords and tokens that expand to existing C/C++ tokens, in such a way that the compiler will assume that the code is perfectly normal.

Many aspects of C and C++ are covered by sea, although you may wish not to use them. For example, the `delete` keyword becomes `dealloc` and the `*` operator can be expanded to by using `point` or `pt`. However, `delete` and `*` are still perfectly usable.

When using sea you may have to define things in your own code with conflict with sea's code. Taking the same example as above, you may wish to use a `point` function or variable, in which case it won't work with sea's `point` token. If that happens to be so, you can simply go into `sea.h`, and modify the tokens defined, or put them as a comment — like so, for example:

sea.h
```cpp
...
#define to       =
// #define point    *
#define out      <<
...
```

Furthermore, some keywords in sea are overwritten, such as the `if` keyword. This means that when using sea, `if` will represent a macro that will expand to another piece of code (in `if`'s case, it expands to the `if` keyword itself, slightly modified — you can check in `sea.h`). Once again, you can modify the name of the macro (to `whatif`, for example...?).

<br />

### sea examples

This example prints "Hello, World!" to the console.
```cpp
#include <iostream>
#include "sea.h"

start run
	
	std sub cout
		out "Hello, World!" __
		
	return 0 __

end run
```

This example creates an integer `a`, which is equal to 10, and a pointer integer `*b` that points to `a`; it also instantiates a pointer `c` which points to 5 on the heap. Then `b` is set to point to `*c`, effectively setting `a` to 5. Eventually all pointers are deallocated, to avoid a memory leak.
```cpp
#include <iostream>
#include "WeirdSyntax.h"

start run

	int a to 10 __
	
	std sub cout 
		out "a = " 
		out a
		out "\n" __
	// "a = 10"
	
	int point b to ref a __
	int point c to new int __
	
	point c to 5 __

	point b to point c __
	
	std sub cout 
		out "a = " 
		out a
		out "\n" __
	// "a = 5"
	
	dealloc c __
	dealloc b __
	
	return 0 __

end run
```
