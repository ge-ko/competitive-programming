# Variables and Functions

## Variable declaration and initialization

In C++ you can store data in the memory by using variables. You can think of
variables as a *name* by which we refer to an address in the memory.

Every variable has a *data type*. The
[type](https://en.cppreference.com/w/cpp/language/types) determines how much
memory it uses (measured in bytes) and what types of operations can be
performed on the data (addition, multiplication, etc).

```cpp
int i;        // -2*10^9 < i < 2*10^9
long j;       // -9*10^18 < j < 9*10^18 -- not portable, see below
long long k;  // -9*10^18 < k < 9*10^18, guaranteed everywhere
bool b;       // b is true and false
string s;     // strings of characters, like "abc"
```

Careful: `long` is not a fixed size in C++, the standard only guarantees it's
at least 32 bits. On Linux and macOS (the data model competitive-programming
judges like HackerRank use) `long` is 64-bit, but on Windows/MSVC it's only
32-bit -- the same size as `int`. Code that relies on `long` holding large
values can silently overflow if compiled on Windows. `long long` is guaranteed
to be at least 64-bit on every platform, so it's the safer default.

Often you will need to choose the type based on the input size. If a number is
less than a billion, choose `int`. If you need to multiply two `int`s or sum a
billion `int`s, choose `long long`. Since numbers are stored in binary format,
knowing some of the powers of 2 is very useful.

```
2^0  =               1
2^1  =               2  = 1 bit = bool
2^2  =               4
2^3  =               8
2^4  =              16
2^5  =              32
2^6  =              64
2^7  =             128
2^8  =             256  = 1 byte = char (can fit an ASCII character)
2^9  =             512
2^10 =           1,024  = 1 Kb >= 10^3
2^11 =           2,048
2^12 =           4,096
2^13 =           8,192
2^14 =          16,384
2^15 =          32,768
2^16 =          65,536  = 2 bytes = wchar (can fit a Unicode character)
...
2^20                    = 1 Mb >= 10^6
2^24 =      16,777,216  = 3 bytes = RGB
...
2^30                    = 1 Gb >= 10^9
2^31 =   2,147,483,647  = int (max signed 4-byte value)
2^32 =   4,294,967,295  = 4 bytes = unsigned int
...
2^40                    = 1 Tb >= 10^12
...
2^50                    = 1 Pb >= 10^15
...
2^60                    = 1 Eb >= 10^18
...
2^63                    = 8 bytes = long long (max signed value)
2^64                    = 8 bytes = unsigned long long
...
2^305                   >= 10^90 >= the information capacity of the universe
```

In order to use a variable it first needs to be defined. It's a good practice
to define the variable as close as possible to where it is used. Variables can
be defined even in loops. They will use the same memory in every iteration of
the loop.

```cpp
int i = 10;
while (i--)
{
    int j = i * i;
    cout << j << '\n';
}
```

Unless initialized, variables contain random data. It's a good practice to
immediately initialize every variable after it is defined.

```cpp
int i = 0;
int n; cin >> n;
for (int i = 0; i < 10; cout << ++i);
```

## Call-by-value or call-by-reference

A *pointer* is a variable that stores the memory address of another variable.
You get the address of a variable with `&`, and you access ("dereference") the
variable a pointer points to with `*`.

```cpp
int i = 10;
int* p = &i;    // p holds the address of i
*p = 20;        // dereferencing p changes i
cout << i;      // 20
```

A *reference* is an alias for another variable -- another name for the same
memory. Unlike a pointer, a reference must be initialized when it's declared
and can never be made to refer to something else afterwards, so there's no
separate dereference syntax; you use it exactly like the variable it refers to.

```cpp
int i = 10;
int& r = i;     // r is another name for i
r = 20;         // changes i, no dereference needed
cout << i;      // 20
```

A *side effect* is anything a function does besides computing and returning a
value -- for example modifying a variable through a reference or pointer,
changing global state, or doing IO.

*Call-by-value* passes a copy of the argument into the function. Changes made
inside the function do not affect the caller's variable.

```cpp
void inc(int i) { ++i; }

int a = 5;
inc(a);
cout << a;      // 5, unaffected -- inc only modified its own copy
```

*Call-by-reference* passes the function a reference (or pointer) to the
caller's variable. Changes made inside the function do affect the caller's
variable -- this is how a function produces a side effect on its argument.

```cpp
void inc(int& i) { ++i; }

int a = 5;
inc(a);
cout << a;      // 6, changed -- inc modified a directly through the reference
```

Follow the
[best practice](https://www.stroustrup.com/bs_faq2.html#call-by-reference):

**To have a side effect, call by reference or use a pointer.** Use a reference
when the argument always exists; use a pointer when the argument is optional,
since a pointer can be `nullptr` and a reference can't.

```cpp
void inc(int& i) { ++i; }                       // i must exist

void inc_if_present(int* i) { if (i) ++*i; }    // i may be nullptr

int a = 5;
inc(a);                  // passes a by reference -- a becomes 6
inc_if_present(&a);      // passes the address of a -- a becomes 7
inc_if_present(nullptr); // does nothing, doesn't crash
```

**No side effect but the parameter is big, call by const reference.** "Big"
means anything more than a few bytes -- `vector`, `string`, and most structs
and classes. Passing by value would copy the whole thing every call; `const&`
avoids the copy while the `const` still stops you from accidentally changing
the caller's data.

```cpp
// v is a reference, so no copy is made; const so v can't be modified
int sum(const vector<int>& v)
{
    int total = 0;
    for (auto e : v) total += e;
    return total;
}
```

**Otherwise, call by value.** For small built-in types -- `int`, `long`,
`double`, `bool`, `char` -- copying is as cheap as passing a reference (they're
usually the same size as a pointer or smaller), so plain call-by-value is
simplest and just as fast.

```cpp
bool is_even(int n)   // n is passed by value -- a free copy to make
{
    return n % 2 == 0;
}
```

One exception worth knowing: a C-style array parameter, e.g. `void f(int a[])`,
doesn't actually copy the array -- it silently decays into a pointer to the
first element. Prefer `vector` or `array` so the parameter type says what it
actually does.

