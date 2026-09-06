# Competitive Programming

I'm creating this repo to provide my son Alex with the basic knowledge to
bootstrap his endeavor in
[competitive programming](https://en.wikipedia.org/wiki/Competitive_programming).

In 2023/2024 he
[ranked 10th](https://soi.ch/contests/2024/round1/ranking-junior/) in the
junior group in the first round of the Swiss Olympiad in Informatics.

## Start coding

Start solving problems in [HackerRank](https://www.hackerrank.com/). HackerRank
provides a code editor, compiler (choose C++14) and a bunch of algorithmic
problems to solve.

To solve a problem that is not on HackerRank, use [repl.it](https://repl.it/).

### Program skeleton

Use this skeleton code to start coding. Put your code in place of the `|`
symbol. Name the file `main.cpp`.

```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(0);

    |
}
```

Every program needs to have a start. In C++ your program starts with the
`main()` function.

Your program will need to use functions from the C++ Standard Library for
input-output, data structures and algorithms. The definition of these functions
is in so-called header files. Header files for the functions that you need must
be included to your program through the `#include` directive. In competitive
programs it is convenient to include just one header file that already includes
all other header files of the C++ Standard Library through
`#include <bits/stdc++.h>`.

You can find a complete reference to the C++ Language and the C++ Standard
Library at [cppreference.com](https://cppreference.com/).

To avoid clashes of functions with the same name in different libraries, C++
provides namespaces. The C++ Standard Library is in the `std` namespace. In
competitive programs it is convenient to have the statement
`using namespace std;` so that all functions can be used directly without the
need to prefix them with `std::`.

In competitive programs you need to input/output data from/to the console as
fast as possible. It's advisable to put the `ios_base::sync_with_stdio(false);`
and `cin.tie(0);` in the beginning of your main function.

### Compiling and running

The C++ source code you write in `main.cpp` is text -- the CPU can't execute it
directly. A *compiler* translates that text into machine code and packages it
into a program you can run, called an *executable*. `g++` is the compiler used
throughout this guide.

```
g++ main.cpp -o main
```

This reads `main.cpp`, and if there are no errors, writes an executable named
`main` (on Windows, `main.exe`). Nothing runs yet -- compiling only builds the
program. To actually run it:

```
./main
```

You can combine the two into one line, so you don't forget to recompile after
changing the code:

```
g++ main.cpp -o main && ./main
```

`&&` means "and, but only if the previous command succeeded" -- so if
compilation fails, `./main` doesn't run a stale, outdated executable.

It's worth adding `-std=c++17` (or whichever standard you're targeting -- see
[Change the C++ version](#change-the-c-version)) so the compiler doesn't fall
back to a default you didn't choose:

```
g++ -std=c++17 main.cpp -o main && ./main
```

**Reading compiler errors.** If your code doesn't compile, `g++` prints the
file, line number, and a description of what's wrong -- read it top to bottom,
since the first error is usually the real one and later ones are often just
fallout from it. For example, forgetting a semicolon:

```
main.cpp: In function 'int main()':
main.cpp:7:5: error: expected ';' before 'return'
    7 |     return 0;
      |     ^~~~~~
```

This means line 7 is where the compiler noticed the problem: it expected a `;`
before `return`, which usually means the *previous* line is missing one.

**Compiling multiple files.** If your program is split across files (e.g.
`main.cpp` and `utils.cpp`), list them all:

```
g++ main.cpp utils.cpp -o main
```

**HackerRank, repl.it, and similar sites** do this for you: their "Run" or
"Submit" button compiles your code with `g++` behind the scenes and runs the
result, showing you the same compiler errors if something goes wrong. Once you
have `./main` running locally, see [Terminal](#terminal) for passing it
arguments, input files, and reading its output.

### Change the C++ version

Every few years a new C++ *standard* is released -- `c++11`, `c++14`, `c++17`,
`c++20`, `c++23` -- each adding new language features on top of the previous
one. HackerRank's "C++14" option, for example, compiles with the `c++14`
standard. Different g++ versions default to different standards (e.g. gcc6
defaults to `gnu++14`), which is exactly why the previous section always passes
`-std=` explicitly rather than relying on the default. Here's how to set it up
so you don't have to type it every time.

#### repl.it

repl.it's C++ template runs your code through a hidden `.replit` file. To
control the standard, show hidden files (the `...` menu in the file list →
*Show hidden files*), open `.replit`, and set the run command to compile with
the flag you want:

```
run = "g++ -std=c++17 main.cpp -o main && ./main"
```

#### Visual Studio Code

If you're compiling from the VS Code terminal, just add the flag to the same
command:

```
g++ -std=c++17 main.cpp -o main && ./main
```

If you've set up a `tasks.json` build task instead, add `-std=c++17` (or
whichever standard you want) to its `args` array.

### Install and configure Visual Studio Code

Follow [these](https://code.visualstudio.com/docs/introvideos/basics)
instructions to install and configure Visual Studio Code, and to start using
it.

Install the [SOI Code](https://soi.ch/wiki/soi-vscode/) extension.

Create `bits/stdc++.h` as instructed
[here](https://github.com/khaveesh/macOS-stdc.h).

### Coding style

Style refers to the way you organize your code so that it can be read and
understood. The style is a matter of personal taste.
[Consistency](https://www.stroustrup.com/bs_faq2.html#layout-style) in using
the same style throughout the program is more important than the specific style
you choose. I encourage you to form your own style.

[Indentation](https://en.wikipedia.org/wiki/Indentation_style) is very
important. I personally prefer 4 spaces indentation. 4 spaces are enough to
visually separate the body and not too much to quickly run out of screen space.

Using spaces is better than tabs, as tabs may be visualized as 4 or 8 spaces
and if mixed with spaces will cause the code to look ugly.

I prefer the
[Allman](https://en.wikipedia.org/wiki/Indentation_style#Allman_style) style,
as it clearly separates control statements from the body, and perhaps because
the first programming language I studied was
[Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language)).

```cpp
int main()
{
    while (x == y)
    {
        something();
        something_else();
    }

    return 0;
}
```

As any true C++ developer, I avoid using capital letters. To name variables, I
use [snake_case](https://en.wikipedia.org/wiki/Snake_case).

### Computer

Computers are machines that execute algorithms (aka instructions, programs or
code) over data. There are many computer architectures, with the most popular
being the
[von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture).
It keeps the code and the data in the same
[memory](https://en.wikipedia.org/wiki/Computer_memory) and has a
[Central Processing Unit (CPU)](https://en.wikipedia.org/wiki/Central_processing_unit)
that executes the code over the data. The memory itself exchanges code and data
with the slower but durable
[mass storage](https://en.wikipedia.org/wiki/Mass_storage) through the Input
and Output.

### Input and output

Your program needs to get input from the user and provide them with an output.
Input and output (IO) can be provided interactively through the
[terminal](https://en.wikipedia.org/wiki/Computer_terminal) or provided in a
batch through files.

To get interactive input use `cin` (*see-in*, from character input). It will
convert the characters to the respective type of the variables. It will skip
through spaces and new lines to get the next variable.

```cpp
int t, n; cin >> t >> n;
```

To provide interactive output, use `cout`. Don't forget to put a new line
`'\n'` wherever needed. You can also use `endl` for a new line but it takes
more time to execute and is better avoided in competitive programming.

```cpp
cout << "t = " << t
     << "\nn = " << n
     << '\n';
cout << endl;
```

To replace interactive IO with batch IO, use files. Create the input file in
advance and fill it in with data. The output file will be created
automatically. The output will be overwritten on every execution of the
program.

```cpp
ifstream in("input.txt");
ofstream out("output.txt");
```

You can run the same program using files with terminal IO by just setting `in`
and `out` to be `cin` and `cout` instead of files.

```cpp
istream in(cin.rdbuf());
ostream out(cout.rdbuf());
// ifstream in("input.txt");
// ofstream out("output.txt");
```

You can mix file and terminal IO. You can also use the special output for
errors `cerr`.

IO has a long history. It started with
[punched cards](https://en.wikipedia.org/wiki/Punched_card) for the input of
data and programs, and
[dot matrix printers](https://en.wikipedia.org/wiki/Dot_matrix_printer) for the
output of the program. Files were stored on
[hard disks](https://en.wikipedia.org/wiki/Hard_disk_drive) and
[magnetic tapes](https://en.wikipedia.org/wiki/Magnetic-tape_data_storage).
[Terminals](https://en.wikipedia.org/wiki/Computer_terminal) introduced the
[keyboard](https://en.wikipedia.org/wiki/Computer_keyboard) and the text-based
[monitor](https://en.wikipedia.org/wiki/Computer_monitor).
[Floppy disks](https://en.wikipedia.org/wiki/Floppy_disk) and
[flash drives](https://en.wikipedia.org/wiki/USB_flash_drive) made it possible
to move data between computers.
[GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) introduced the
graphical monitor and the
[pointing device](https://en.wikipedia.org/wiki/Pointing_device) (like the
mouse). [Networks](https://en.wikipedia.org/wiki/Computer_network) made it even
easier to move data between computers.

Text-based IO through the terminal and files are commonly used in competitive
programming. GUI and networks are not used.

### Terminal

`cin`, `cout`, and `cerr` are covered above in
[Input and output](#input-and-output). This section covers the rest of how a
program talks to the terminal: command-line parameters, the return value, and
code that runs before `main()`.

#### Command-line parameters

`main` can optionally take two parameters: the number of command-line arguments
and the arguments themselves. `argv[0]` is always the program's own name, so
the actual arguments start at `argv[1]`.

```cpp
int main(int argc, char* argv[])
{
    for (int i = 0; i < argc; ++i)
        cout << argv[i] << '\n';
}
```

After compiling (`g++ main.cpp -o main`), everything above comes from how you
run `./main` in the terminal.

**Passing arguments.** Anything you type after the program name becomes an
element of `argv`, split on whitespace.

```
./main hello 42
```

Here `argc` is `3`: `argv[0]` is `./main`, `argv[1]` is `"hello"`, `argv[2]` is
`"42"`. Note that `argv[2]` is the *string* `"42"`, not the number 42 -- if you
need it as a number, convert it yourself, e.g. `atoi(argv[2])`.

**Redirecting input with `<`.** Instead of typing input by hand at `cin`, feed
it from a file:

```
./main < input.txt
```

The program can't tell the difference -- `cin` reads from `input.txt` exactly
as if you'd typed its contents into the terminal.

**Redirecting output with `>` and `>>`.** Send `cout` to a file instead of the
screen. `>` overwrites the file each time; `>>` appends to it.

```
./main > output.txt     # overwrite output.txt with the program's output
./main >> output.txt    # append the program's output to output.txt
./main < input.txt > output.txt   # combine both: read a file, write a file
```

`cerr` isn't affected by `>` -- it still prints to the terminal, which is
exactly why errors go to `cerr` and normal output goes to `cout`: you can
redirect one without losing the other. To redirect `cerr` too, use `2>`.

**Piping with `|`.** Instead of a file, connect one program's output directly
to another program's input. This is handy for comparing your program's output
against expected output.

```
./main < input.txt | diff - expected.txt
```

**Checking the result with `$?`.** After a program finishes, `$?` holds the
return value from `main` (see [Return value](#return-value) below). This is how
scripts detect success or failure.

```
./main
echo $?     # prints 0 if main returned 0 (success), non-zero otherwise
```

#### Return value

`main` returns an `int` to the operating system. `0` conventionally means the
program succeeded; any other value signals an error. If you don't write a
`return` statement, the compiler inserts `return 0;` for you.

```cpp
int main()
{
    int n; cin >> n;
    if (n < 0) return 1;   // signal failure to whatever ran the program

    cout << n << '\n';
    // return 0; is implicit here
}
```

#### Code that runs before main()

Global and `static` variables are initialized before `main()` starts running.
This can be used to run code before `main()`, but the initialization order
across different files is unspecified, so don't rely on one global depending on
another having already run.

```cpp
int setup = []{ cout << "before main\n"; return 42; }();  // runs before main()

int main()
{
    cout << setup << '\n';   // 42
}
```

#### Exceptions

Exceptions are a mechanism for signaling and handling errors: `throw` an
exception, and the nearest matching `catch` handles it, unwinding the call
stack in between. They're rarely used in competitive programming, since contest
input is assumed to be well-formed, but they're worth knowing.

```cpp
try
{
    int n; cin >> n;
    if (n == 0) throw runtime_error("n cannot be 0");
    cout << 100 / n << '\n';
}
catch (const exception& e)
{
    cerr << e.what() << '\n';
}
```

### Variable declaration and initialization

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

### Call-by-value or call-by-reference

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

### Vector

Vectors are multiple variables stored contiguously in the memory. Each variable
in the vector has an index starting at 0.

```cpp
vector<int> a(10);                      // a vector of 10 elements of type int
for (int i = 0; i < (int)a.size(); ++i) // cast avoids signed/unsigned warning
{
    a[i] = i + 1;                       // assign the i-th element of the vector
}
a.push_back(11);                        // add another element to the back
a.push_back(12);                        // and another one
cout << a[0] + a[4] + a[11] << '\n';    // 18 = 1st + 5th + 12th elements
```

Most C++ Standard Library algorithms operate on a range, given as a pair of
begin and end iterators. In competitive programming it's convenient to replace
`v.begin(), v.end()` with a single macro:

```cpp
#define all(c) (c).begin(), (c).end()
```

```cpp
sort(all(a));           // instead of sort(a.begin(), a.end());
```

## Complexity

Programs have certain input. The size of the input may vary. Usually the size
depends on one or more variables. Very often it is one variable called `n`.

The program complexity shows how the time and space (or memory) used by the
program correspond to the input size.

```cpp
#include <bits/stdc++.h>
using namespace std;

// O(1) - constant time and space
// Does not grow with n
// Example: Find the Answer to the Ultimate Question of
//          Life, the Universe, and Everything
// https://simple.wikipedia.org/wiki/42_(answer)
int the_answer()
{
    return 42;
}

// O(log n) - logarithmic time and space
// Grows as fast as the base-2 logarithm of n
// Example: Find the binary digits of a number
vector<int> bits(int n)
{
    vector<int> result;
    for (int i = n; i > 0; i /= 2)
        result.push_back(i % 2);
    return result;
}

// O(sqrt n) - fractional time and space
// Grows as fast as the square root of n
// Example: Find the divisors of a number
vector<int> divisors(int n)
{
    vector<int> result;
    int sqrt_n = sqrt(n);
    for (int i = 1; i <= sqrt_n; ++i)
    {
        if (n % i == 0)                     // if i is a divisor of n
        {
            if (i * i == n)                 // if n is a perfect square
            {
                result.push_back(i);        // sqrt_n has no counterpart
            }
            else                            // all other divisors come in pairs
            {
                result.push_back(i);
                result.push_back(n / i);
            }
        }
    }
    return result;
}

// O(n) - linear time and space
// Grows as fast as n
// Example: Traverse a vector, Maximum subarray
// https://soi.ch/wiki/algorithms-intro/#example-maximum-subarray
istream& operator>>(istream& is, vector<int>& v)
{
    for (auto& e : v)
        is >> e;
    return is;
}
ostream& operator<<(ostream& os, const vector<int>& v)
{
    for (auto e : v)
        os << e << ' ';
    return os;
}
int max_subarray_sum(const vector<int>& v)
{
    int bordermax = 0, totalmax = 0;
    for (auto e : v)
    {
        bordermax += e;
        bordermax = max(bordermax, 0);
        totalmax = max(totalmax, bordermax);
    }
    return totalmax;
}

// O(n log n) - linearithmic time and space
// Grows as fast as n * log n
// Example: Merge sort
void merge_sort(vector<int>& v)
{
    if (v.size() < 2) return;
    vector<int> left(v.begin(), v.begin() + v.size() / 2);
    merge_sort(left);
    vector<int> right(v.begin() + v.size() / 2, v.end());
    merge_sort(right);
    merge(left.begin(), left.end(), right.begin(), right.end(), v.begin());
}

// O(n^2) - quadratic time and space
// Grows as fast as n^2
// Example: Traverse a matrix, Bubble sort
using matrix = vector<vector<int>>;
istream& operator>>(istream& is, matrix& m)
{
    for (auto& v : m)
        is >> v;
    return is;
}
ostream& operator<<(ostream& os, const matrix& m)
{
    for (auto v : m)
        os << v << '\n';
    return os;
}
void bubble_sort(vector<int>& v)
{
    for (int i = 0; i < (int)v.size(); ++i)
        for (int j = 1; j < (int)v.size() - i; ++j)
            if (v[j - 1] > v[j])
                swap(v[j - 1], v[j]);
}

// O(n^3) - cubic time and space
// Grows as fast as n^3
// Example: Matrix multiplication
// https://en.wikipedia.org/wiki/Matrix_multiplication
matrix operator*(const matrix& a, const matrix& b)
{
    int m = a.size(), n = b.size(), p = b[0].size();
    matrix r(m, vector<int>(p));
    for (int i = 0; i < m; ++i)
        for (int j = 0; j < p; ++j)
        {
            r[i][j] = 0;
            for (int k = 0; k < n; ++k)
                r[i][j] += a[i][k] * b[k][j];
        }
    return r;
}

// O(2^n) - exponential time and space
// Grows as fast as 2^n
// Example: Find all subsets of a vector
vector<vector<int>> powerset(const vector<int>& v)
{
    vector<vector<int>> result;
    result.push_back(vector<int>());        // start with the empty set

    for (auto e : v)                        // for each element in v
    {
        vector<vector<int>> copy = result;  // copy all subsets so far
        for (auto s : copy)
        {
            s.push_back(e);                 // append the element to each subset
            result.push_back(s);            // append it to the result
        }
    }
    return result;
}

// O(n!) - factorial time and space
// Grows as fast as n!
// Example: Find all permutations of a vector
vector<vector<int>> permutations(vector<int>& v)
{
    vector<vector<int>> result;
    sort(v.begin(), v.end());               // next_permutation needs this
    result.push_back(v);

    while (next_permutation(v.begin(), v.end()))
    {
        result.push_back(v);
    }
    return result;
}

int main()
{
    // O(1) - constant time and space
    cout << the_answer() << '\n';

    // O(log n) - logarithmic time and space
    cout << bits(the_answer()) << '\n';

    // O(sqrt n) - fractional time and space
    cout << divisors(the_answer()) << '\n';

    // O(n) - linear time and space
    cout << max_subarray_sum({5, 7, 12, -48, 9, 36, -17, 22,
                              11, -49, 49, -49, 111, -117}) << '\n';

    // O(n log n) - linearithmic time and space
    vector<int> v = {3, 1, 2};
    merge_sort(v);
    cout << v << '\n';

    // O(n^2) - quadratic time and space
    vector<int> u = {3, 1, 4, 2, 5};
    bubble_sort(u);
    cout << u << '\n';

    // O(n^3) - cubic time and space
    matrix a =
    {
        {1, 0, 1},
        {2, 1, 1},
        {0, 1, 1},
        {1, 1, 2}
    };
    matrix b =
    {
        {1, 2, 1},
        {2, 3, 1},
        {4, 2, 2}
    };

    matrix r = a * b;
    cout << r << '\n';

    // O(2^n) - exponential time and space
    cout << powerset(v) << '\n';

    // O(n!) - factorial time and space
    cout << permutations(v) << '\n';
}
```

Modern processors run at around 4 GHz clock speed. They can execute roughly 4
billion operations in a second. The runtime of an `O(n)` algorithm for
`n <= 2^32` will be a few seconds, which is acceptable. However, for
`n <= 2^64`, the runtime would be roughly 100 years.

Choose the right algorithm for the input constraints of the problem.

| input size   | complexity     | examples              |
| ------------ | -------------- | ---------------------- |
| n <= 11      | O(n!)          | Permutations           |
| n <= 32      | O(2^n)         | Power set               |
| n <= 10^3    | O(n^3)         | Matrix multiplication  |
| n <= 5\*10^4 | O(n^2)         | Bubble sort             |
| n <= 10^6    | O(n log n)     | Merge sort              |
| n <= 10^9    | O(n)           | Maximum subarray        |
| n <= 10^18   | O(sqrt n)      | Divisors                |
| n > 10^18    | O(log n), O(1) | Binary search           |

## Graphs

(source <https://soi.ch/wiki/graphs/>)

A graph is a set of points and connections between those points. A point is
usually called a *node* or *vertex*, and for a connection, we use the term
*edge*.

Nodes are usually numbered from `1` to `n`. For simplicity we assume here that
nodes are numbered from `0` to `n-1`. If that is not the case, adjust numbering
by adding/subtracting `1` or by skipping the `0` node.

Two nodes are *adjacent* or *neighbors* if they are connected through an edge.
Not every two nodes need to be connected.

Graphs can be directed or undirected. Undirected graphs have a bi-directional
connection between every two nodes they connect. Directed graphs may have
one-way connections between nodes.

A path between two nodes is a list of unique nodes (including the two nodes)
such that all the nodes in the path are connected. If there is no path between
two nodes, they belong to different connected components. If a path exists from
a node to itself, there is a cycle in the graph.

A tree is an acyclic connected graph. A forest is an acyclic graph.

Edges may have an associated weight that can be used to describe things like
length of roads, price of airplane tickets, etc.

### How to store a graph?

There are two common ways to store graphs in memory: *adjacency list* and
*adjacency matrix*. They have different space and time tradeoffs.

| space / time                | adjacency list | adjacency matrix |
| ---------------------------- | -------------- | ------------------ |
| storage                      | O(n+m)         | O(n^2)             |
| insert edge                  | O(1)           | O(1)               |
| delete edge                  | O(degree)      | O(1)               |
| check if edge exists         | O(degree)      | O(1)               |
| find all edges from a node   | O(degree)      | O(n)               |
| traverse graph (BFS/DFS)     | O(n+m)         | O(n^2)             |

#### Adjacency list

The most common way to store a graph is a so-called *adjacency list*. For every
node you store a list of all of its neighbors. If the graph is undirected, for
each connected pair of nodes `a` and `b` store two directed edges: from `a` to
`b` and from `b` to `a`.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

int n; cin >> n;
graph g(n);

int m; cin >> m;
while (m--)
{
    int a, b; cin >> a >> b;
    g[a].push_back(b);
    g[b].push_back(a);
}
```

To print a graph, overload `ostream::operator<<`.

```cpp
ostream& operator<<(ostream& os, const neighbors& n)
{
    bool first = true;
    for (auto u : n)
    {
        if (!first) os << ",";
        first = false;
        os << u;
    }
    return os;
}
ostream& operator<<(ostream& os, const graph& g)
{
    for (int i = 0; i < (int)g.size(); ++i)
    {
        os << i << ": " << g[i] << '\n';
    }
    return os;
}

int main()
{
    ...

    cout << g;  // prints the whole graph
}
```

If you need to store edge weights, use a `pair`.

```cpp
using weight = int;
using node = int;
using edge = pair<weight, node>;
using neighbors = vector<edge>;
using graph = vector<neighbors>;

int n; cin >> n;
graph g(n);

int m; cin >> m;
while (m--)
{
    int a, b, w; cin >> a >> b >> w;
    g[a].push_back(make_pair(w, b));
}
```

#### Adjacency matrix

In an *adjacency matrix*, rows and columns represent the nodes and the cell at
row `a` and column `b` represents the edge between node `a` and node `b`. You
can either use `bool` to encode the presence or absence of an edge between `a`
and `b`, or `int` to encode the weight of the edge between `a` and `b`.

```cpp
using weight = int;
using nodes = vector<weight>;
using graph = vector<nodes>;

int n; cin >> n;
graph g(n, nodes(n, 0));  // initialize the whole matrix with weight 0

int m; cin >> m;
while (m--)
{
    int a, b, w; cin >> a >> b >> w;
    g[a][b] = w;
}
```

### Graph algorithms

Popular graph algorithms are used to traverse the whole graph in a specific
order or to find a (minimal) path to a node. Graph algorithms are often greedy
algorithms. They descend to the first neighbor with some specific
characteristic:

- the node attached to the last visited node (DFS)
- the node with the least number of edges from the start (BFS)
- the node with the shortest path from the start (Dijkstra)
- the node that has the shortest distance *by air* from the start (A*)

Graph algorithms have a common structure.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> graph_algo(const graph& g)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    sequencer s; // stack, queue, priority_queue
    s.push(0);   // start at node 0

    while (!s.empty())
    {
        node v = s.top();
        s.pop();

        // skip visited
        if (visited[v]) continue;

        // visit
        visited[v] = true;
        path.push_back(v);

        for (node u : g[v]) // for each neighbor
        {
            s.push(u);
        }
    }

    return path;
}
```

The `sequencer` is a data structure that enforces a specific traversal order.

### Graph traversal algorithms

#### Depth-first search (DFS)

Depth-first search (DFS) is a traversal algorithm that uses a `stack`.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> dfs(const graph& g)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    vector<node> s; // vector used as a stack
    s.push_back(0);

    while (!s.empty())
    {
        node v = s.back();
        s.pop_back();

        // skip visited
        if (visited[v]) continue;

        // visit
        visited[v] = true;
        path.push_back(v);

        for (node u : g[v]) // for each neighbor
        {
            s.push_back(u);
        }
    }

    return path;
}
```

The algorithm can also use the call stack to store the next elements to visit.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

void dfs(const graph& g, node v, vector<bool>& visited,
         vector<node>& path)
{
    // skip visited
    if (visited[v]) return;

    // visit
    visited[v] = true;
    path.push_back(v);

    for (node u : g[v]) // for each neighbor
    {
        dfs(g, u, visited, path);   // pushes u onto the call stack
    }
}

vector<node> dfs(const graph& g)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    dfs(g, 0, visited, path);

    return path;
}
```

#### Breadth-first search (BFS)

Breadth-first search (BFS) is a traversal algorithm that uses a `queue`.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> bfs(const graph& g)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    queue<int> q;
    q.push(0);

    while (!q.empty())
    {
        node v = q.front();
        q.pop();

        // skip visited
        if (visited[v]) continue;

        // visit
        visited[v] = true;
        path.push_back(v);

        for (node u : g[v]) // for each neighbor
        {
            q.push(u);
        }
    }

    return path;
}
```

### Shortest path algorithms

#### Dijkstra

Dijkstra is a traversal algorithm that uses a `priority_queue` to find the
shortest path from a start node to all connected nodes, or to a specific finish
node.

Google Maps uses the Dijkstra algorithm to show shortest distance between
source and destination.

```cpp
using weight = int;
using node = int;
using edge = pair<weight, node>;
using neighbors = vector<edge>;
using graph = vector<neighbors>;

vector<node> dijkstra(const graph& g, node start, node finish)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    vector<int> dist(n, INT_MAX);   // INT_MAX == +infinity
    dist[start] = 0;

    // min-heap, ordered by dist[v]
    priority_queue<edge, vector<edge>, greater<edge>> pq;
    pq.push(make_pair(0, start));

    while (!pq.empty())
    {
        node v = pq.top().second;   // the node with shortest path from start
        pq.pop();

        if (visited[v]) continue;

        // visit
        visited[v] = true;
        path.push_back(v);

        if (v == finish) break;   // remove to traverse the whole graph

        for (edge e : g[v])
        {
            weight w = e.first;
            node u = e.second;
            if (dist[u] <= dist[v] + w) continue;   // not a better path

            dist[u] = dist[v] + w;
            pq.push(make_pair(dist[u], u));
        }
    }

    return path;
}
```

#### A*

A* is Dijkstra plus a *heuristic*: an estimate `h[v]` of the remaining cost
from node `v` to `finish`. Instead of exploring nodes purely by distance from
the start (like Dijkstra), A* explores nodes by `dist[v] + h[v]`, so it's
pulled towards the finish instead of spreading out evenly in every direction. A
classic example is pathfinding on a grid, where `h[v]` is the straight-line
(Euclidean) or grid (Manhattan) distance from `v` to the target.

The heuristic must never *overestimate* the true remaining cost (it must be
*admissible*), otherwise A* is no longer guaranteed to find the shortest path.
An `h` that is always `0` makes A* behave exactly like Dijkstra.

```cpp
using weight = int;
using node = int;
using edge = pair<weight, node>;
using neighbors = vector<edge>;
using graph = vector<neighbors>;

// h[v] estimates the remaining cost from v to finish; must never overestimate
vector<node> a_star(
    const graph& g, node start, node finish, const vector<weight>& h)
{
    int n = g.size();
    vector<bool> visited(n, false);
    vector<node> path;

    vector<int> dist(n, INT_MAX);
    dist[start] = 0;

    // min-heap, ordered by dist[v] + h[v]
    priority_queue<edge, vector<edge>, greater<edge>> pq;
    pq.push(make_pair(h[start], start));

    while (!pq.empty())
    {
        node v = pq.top().second;
        pq.pop();

        if (visited[v]) continue;

        visited[v] = true;
        path.push_back(v);

        if (v == finish) break;   // remove to traverse the whole graph

        for (edge e : g[v])
        {
            weight w = e.first;
            node u = e.second;
            if (dist[u] <= dist[v] + w) continue;   // not a better path

            dist[u] = dist[v] + w;
            pq.push(make_pair(dist[u] + h[u], u));
        }
    }

    return path;
}
```

On a 2D grid, node `v` maps to row `v / cols` and column `v % cols`. Two common
choices for `h`, depending on which directions you can move in:

```cpp
// admissible when movement is up/down/left/right only (4 directions)
weight manhattan_distance(node v, node finish, int cols)
{
    int v_row = v / cols, v_col = v % cols;
    int f_row = finish / cols, f_col = finish % cols;
    return abs(v_row - f_row) + abs(v_col - f_col);
}

// admissible for any movement, including diagonals;
// floor() keeps it from overestimating
weight euclidean_distance(node v, node finish, int cols)
{
    int v_row = v / cols, v_col = v % cols;
    int f_row = finish / cols, f_col = finish % cols;
    return (weight)floor(hypot(v_row - f_row, v_col - f_col));
}
```

Build `h` once, before calling `a_star`:

```cpp
int rows, cols; cin >> rows >> cols;
node finish = ...;

vector<weight> h(rows * cols);
for (node v = 0; v < rows * cols; ++v)
    h[v] = manhattan_distance(v, finish, cols);   // or euclidean_distance
```

### Union-find (aka Disjoint Set Union - DSU)

*Union-find* is a data structure that helps manage a collection of disjoint
sets. It does that by associating each component of the graph with a
representative node (aka the *chef*) and checking whether two nodes belong to
the same component.

*Union-find* has two operations:

- `find` - finds the *chef* of a node
- `unite` - creates a union between two components

```cpp
using node = int;

struct ufind
{
    // holds the chef of a non-chef node,
    // or -size of the component for chef nodes
    vector<node> c;
    // each node starts as its own component of size 1 (stored as -1)
    ufind(int n) : c(n, -1) {}

    int find(node k)
    {
        return c[k] < 0 ? k : c[k] = find(c[k]);
    }

    void unite(node a, node b)
    {
        a = find(a); b = find(b);
        if (a == b) return; // a and b are already in the same component
        if (c[a] > c[b]) swap(a, b);
        c[a] += c[b];
        c[b] = a;
    }
};
```

### Minimum Spanning Tree (MST)

An `MST` is a subset of edges that connects all vertices in a *connected*,
*weighted* graph without cycles, with the minimum possible total edge *cost*
(weight).

#### Kruskal's algorithm

Kruskal's algorithm is a greedy algorithm, which sorts the edges by *cost* and,
for each edge in that order, checks whether adding it would create a cycle. It
does that using *Union-Find*.

```cpp
using cost = int;
using node = int;
using edge = pair<cost, pair<node, node>>;
// graph stores edges as individual elements of a vector
using graph = vector<edge>;

graph kruskal(graph& g, int n)
{
    graph mst;
    // initializes dsu with n - number of nodes
    ufind dsu(n);
    // sorts edges by cost
    sort(g.begin(), g.end());
    for (auto e : g)
    {
        node u = e.second.first;
        node v = e.second.second;
        cost c = e.first;
        if (dsu.find(u) == dsu.find(v)) continue;
        dsu.unite(u, v);
        mst.push_back({c, {u, v}});
    }
    return mst;
}
```

#### Prim's algorithm

Prim's algorithm is very similar to `Dijkstra's`. It uses a priority queue to
sort all edges as they're pushed into it. Each edge popped from the queue gets
added to the MST only if the node it leads to has never been visited before. We
then take that node's neighboring edges and push them onto the queue.

```cpp
using node = int;
using cost = int;
using edge = pair<cost, pair<node, node>>;
using neighbors = vector<edge>;
using graph = vector<neighbors>;

vector<edge> prim(const graph& g)
{
    vector<edge> mst;

    int n = g.size();
    vector<bool> visited(n, false);
    visited[0] = true;

    priority_queue<edge, vector<edge>, greater<edge>> pq;
    for (auto& o : g[0]) pq.push(o);

    while (!pq.empty())
    {
        edge i = pq.top();
        node v = i.second.second;
        pq.pop();

        if (visited[v]) continue;
        visited[v] = true;

        mst.push_back(i);

        for (auto& o : g[v]) pq.push(o);
    }
    return mst;
}
```

### Topological sort

The topological sort algorithm, given tasks that depend on one another, returns
the tasks in an order such that every task comes after all the tasks it depends
on. This can be represented as a directed graph.

#### Kahn's algorithm

Kahn's algorithm does a topological sort by computing an `indegree` for each
node (the number of nodes pointing at that node). It then pushes onto a queue
only the nodes with `indegree = 0` (they don't depend on other nodes). It
repeatedly pops a node from the queue, appends it to the topological order, and
for each of that node's neighbors decrements their `indegree`, pushing any that
reach `indegree = 0` onto the queue.

```cpp
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> kahn(const graph& g)
{
    int n = g.size();
    vector<int> indegree(n, 0);
    // sets indegree for each node
    for (node u = 0; u < n; ++u)
        for (auto v : g[u])
            ++indegree[v];

    queue<node> q;
    // pushes all nodes with indegree = 0
    for (node u = 0; u < n; ++u)
        if (indegree[u] == 0) q.push(u);

    vector<node> toposort;
    while (!q.empty())
    {
        node u = q.front();
        q.pop();

        // adds node to the topological sort
        toposort.push_back(u);

        for (auto v : g[u])
        {
            // decrements indegree
            --indegree[v];
            // pushes all nodes with new indegree = 0
            if (indegree[v] == 0) q.push(v);
        }
    }

    // toposort.size() < n means there is a cycle
    return (int)toposort.size() == n ? toposort : vector<node>{};
}
```

