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
