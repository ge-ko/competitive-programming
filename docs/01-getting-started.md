# Getting Started

## Start coding

Start solving problems in [HackerRank](https://www.hackerrank.com/). HackerRank
provides a code editor, compiler (choose C++14) and a bunch of algorithmic
problems to solve.

To solve a problem that is not on HackerRank, use [repl.it](https://repl.it/).

## Program skeleton

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

## Compiling and running

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
result, showing you the same compiler errors if something goes wrong. Once
you have `./main` running locally, see
[Terminal](03-the-computer.md#terminal) for passing it arguments, input
files, and reading its output.

## Change the C++ version

Every few years a new C++ *standard* is released -- `c++11`, `c++14`, `c++17`,
`c++20`, `c++23` -- each adding new language features on top of the previous
one. HackerRank's "C++14" option, for example, compiles with the `c++14`
standard. Different g++ versions default to different standards (e.g. gcc6
defaults to `gnu++14`), which is exactly why the previous section always passes
`-std=` explicitly rather than relying on the default. Here's how to set it up
so you don't have to type it every time.

### repl.it

repl.it's C++ template runs your code through a hidden `.replit` file. To
control the standard, show hidden files (the `...` menu in the file list →
*Show hidden files*), open `.replit`, and set the run command to compile with
the flag you want:

```
run = "g++ -std=c++17 main.cpp -o main && ./main"
```

### Visual Studio Code

If you're compiling from the VS Code terminal, just add the flag to the same
command:

```
g++ -std=c++17 main.cpp -o main && ./main
```

If you've set up a `tasks.json` build task instead, add `-std=c++17` (or
whichever standard you want) to its `args` array.

## Install and configure Visual Studio Code

Follow [these](https://code.visualstudio.com/docs/introvideos/basics)
instructions to install and configure Visual Studio Code, and to start using
it.

Install the [SOI Code](https://soi.ch/wiki/soi-vscode/) extension.

Create `bits/stdc++.h` as instructed
[here](https://github.com/khaveesh/macOS-stdc.h).

