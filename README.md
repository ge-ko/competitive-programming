# Competitive Programming

I'm creating this repo to provide my son Alex with the basic knowledge to bootstrap his endeavor in [competitive programming](https://en.wikipedia.org/wiki/Competitive_programming).

## Start coding

Start solving problems in [HackerRank](https://www.hackerrank.com/). It provides a code editor, compiler (choose C++20) and a bunch of algorithmic problems to solve.

To solve a problem on your own, use [repl.it](https://repl.it/).

Later I will explain how to install and configure Visual Studio Code on your laptop.

## Skeleton program

Use this skeleton code to start coding. Put your code in place of the `|` symbol. Name the file `main.cpp`.

```c++
#include <bits/stdc++.h>
using namespace std;
#define all(c) (c).begin(), (c).end()

int main()
{
    ios_base::sync_with_stdio(false);
    cin.tie(0);

    |
}
```

Every program needs to have a start. In C++ your program starts with the `main()` function. Later I will provide more details on passing parameters to your program, getting a return value from your program, executing code even before `main()`, exceptions and many more.

Your program will need to use functions from the C++ Standard Library for input-output, data structures and algorithms. The definition of these functions is in so-colled header files. Header files for the functions that you need must be included to your program through the `#include` directive. In competitive programs it is convenient to include just one header file that already includes all other header files of the C++ Standard Library through `#include <bits/stdc++.h>`.

You can find a complete reference to the C++ Language and the C++ Standard Library at [cppreference.com](https://cppreference.com/).

To avoid name clashes of functions between different libraries C++ provides namespaces. The C++ Standard Library is in the namespace `std`. In competitive programs it is convenient to have the statement `using namespace std;` so that all functions can be used directly without the need to prefix them with `std::`.

All algorithms in the C++ Standard Library that iterate over data structures accept a pair of iterators to begin at and end at. In competitive programs it is convenient to replace that code with just `all()`. That's why we need to define this macro: `#define all(c) (c).begin(), (c).end()`.

In competitive programs we need to input and output data as fast as possible. It's advisable to put the ` ios_base::sync_with_stdio(false);` and `cin.tie(0);` in the beginning of your main function.

## Coding style

TODO

function body on the next line

variables in snake case

4 space indent

## Input-output (I/O)

TODO

`cin`, `cout`, file I/O

## Variable declaratio and initialization

TODO

```c++
    int i = 0;
    int n; cin >> n;
```
