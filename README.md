# Competitive Programming

I'm creating this repo to provide my son Alex with the basic knowledge to bootstrap his endeavor in [competitive programming](https://en.wikipedia.org/wiki/Competitive_programming).

## Start coding

Start solving problems in [HackerRank](https://www.hackerrank.com/). HackerRank provides a code editor, compiler (choose C++14) and a bunch of algorithmic problems to solve.

To solve a problem that is not on HackerRank, use [repl.it](https://repl.it/).

## Program skeleton

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

Your program will need to use functions from the C++ Standard Library for input-output, data structures and algorithms. The definition of these functions is in so-called header files. Header files for the functions that you need must be included to your program through the `#include` directive. In competitive programs it is convenient to include just one header file that already includes all other header files of the C++ Standard Library through `#include <bits/stdc++.h>`.

You can find a complete reference to the C++ Language and the C++ Standard Library at [cppreference.com](https://cppreference.com/).

To avoid name clashes of functions between different libraries C++ provides namespaces. The C++ Standard Library is in the namespace `std`. In competitive programs it is convenient to have the statement `using namespace std;` so that all functions can be used directly without the need to prefix them with `std::`.

All algorithms in the C++ Standard Library that iterate over data structures accept a pair of iterators to begin at and end at. In competitive programs it is convenient to replace that code with just `all()`. That's why we need to define this macro: `#define all(c) (c).begin(), (c).end()`.

In competitive programs we need to input and output data as fast as possible. It's advisable to put the `ios_base::sync_with_stdio(false);` and `cin.tie(0);` in the beginning of your main function.

## Coding style

Style refers to the way you organize your code so that it can be read and understood. The style is a matter of personal taste. [Consistency](https://www.stroustrup.com/bs_faq2.html#layout-style) in using the same style throughput the program is more important then the specific style you choose. I encourage you to form your own style.

[Indentation](https://en.wikipedia.org/wiki/Indentation_style) is very important. I personally prefer 4 spaces indentation. 4 spaces are enough to visually separate the body and not too much to quickly run out of screen space.

Using spaces is better than tab as tabs may be visualized as 4 or 8 spaces and if mixed with spaces will cause the code to look ugly.

I prefer the [Allman](https://en.wikipedia.org/wiki/Indentation_style#Allman_style) style as it clearly separates control statements from the body and perhaps because the first programming language is studied was [Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language)).

```c++
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

As any true C++ developer, I avoid using capital letters. To name variables, I use [snake_case](https://en.wikipedia.org/wiki/Snake_case).

## Input and output (I/O)

Your program needs to get input from the user and provide them with an output. Input and output (I/O) can be provided interactively through the [terminal](https://en.wikipedia.org/wiki/Computer_terminal) or provided in a batch through files.

To get interactive input use `cin` (*see-in*, from character input). It will convert the characters to the respective type of the variables. It will skip through spaces and new lines to get the next variable.

```c++
    int t, n; cin >> t >> n;
```

To provide interactive output, use `cout`. Don't forget to put a new line `'\n'` wherever needed. You can also use `endl` for a new line but it takes more time to execute and is better avoided in competitive programming.

```c++
    cout << "t = " << t
         << "\nn = " << n
         << '\n';
    cout << endl;
```

To replace interactive IO with batch IO, use files. Create the input file in advance and fill it in with data. The output file will be created automatically. The output will be overwritten on every execution of the program.

```c++
    ifstream in("input.txt");
    ofstream out("output.txt");
```

You can have the same program using the terminal and files by just replacing `in` and `out` to be `cin` and `cout` instead of files.

```c++
    istream in(cin.rdbuf());
    ostream out(cout.rdbuf());
//    ifstream in("input.txt");
//    ofstream out("output.txt");
```

You can mix file in terminal IO. You can also use the special output for errors `cerr`.

IO has a long history. It started with [punched cards](https://en.wikipedia.org/wiki/Punched_card) and [dot matrix printers](https://en.wikipedia.org/wiki/Dot_matrix_printer). Files were stored on [hard disks](https://en.wikipedia.org/wiki/Hard_disk_drive) and [magnet tapes](https://en.wikipedia.org/wiki/Magnetic-tape_data_storage). [Terminals](https://en.wikipedia.org/wiki/Computer_terminal) introduced the [keyboard](https://en.wikipedia.org/wiki/Computer_keyboard) and the text-based [monitor](https://en.wikipedia.org/wiki/Computer_monitor). [Floppy disks](https://en.wikipedia.org/wiki/Floppy_disk) and [flash drives](https://en.wikipedia.org/wiki/USB_flash_drive) made possible to move data between computers. [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) introduced the graphical monitor and the [pointing device](https://en.wikipedia.org/wiki/Pointing_device) (like the mouse). [Networks](https://en.wikipedia.org/wiki/Computer_network) made it more easy to move data between computers.

Text-based IO through the terminal and files are commonly used in competitve programming. GUI and networks are not used.

## Variable declaration and initialization

In C++ you can store data in the memory by using variables. Variables are like *labels* that allow us to refer to the memory where we have stored the data.

Every variable has a *data type*. The [type](https://en.cppreference.com/w/cpp/language/types) determines how much memory it uses (measured in bytes) and what types of operations can be performed on the data (addition, multiplication, etc).

```c++
    int i;      // -2*10^9 < i < 2*10^9
    long j;     // -9*10^18 < j < 9*10^18
    bool b;     // b is true and false
    string s;   // strings of characters, like "abc"
```

In order to use a variable it first needs to be defined. It's a good practice to define the variable as close as possible to where it is used. Variables can be defined even in loops. They will use the same memory in every iteration of the loop.

```c++
    int i = 10;
    while (i--)
    {
        int j = i * i;
        cout << j << '\n';
    }
```

Unless initialized, variables contain random data. It's a good practice to immediately initialize every variable after it is defined.

```c++
    int i = 0;
    int n; cin >> n;
    for (int i = 0; i < 10; cout << ++i);
```

## Install and configure Visual Studio Code

Follow [these](https://code.visualstudio.com/docs/introvideos/basics) instructions to install Visual Studio Code.

Install the [SOI Code](https://soi.ch/wiki/soi-vscode/) extension.

## TODO

The next sections are not complete

## Call-by-value or call-by-reference

Explain pointer type
Explain reference type
Explain what side effect is
Explain call-by-value and call-by-reference
Explain the [best practice](https://www.stroustrup.com/bs_faq2.html#call-by-reference):

* To have a side effect call by reference or use a pointer; e.g. void f(type&); or void f(type*);
* No side effect but the parameter is big, call by const reference; e.g. void f(const type&);
* Otherwise, call by value; e.g. void f(type);

## Change the C++ version

repl.it
vscode
<https://replit.com/@GeorgiKostov/cver>

## Terminal

parameters, return value, cin, cout, cerr.
