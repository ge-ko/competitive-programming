# The Computer

## Computer

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

## Input and output

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

## Terminal

`cin`, `cout`, and `cerr` are covered above in
[Input and output](#input-and-output). This section covers the rest of how a
program talks to the terminal: command-line parameters, the return value, and
code that runs before `main()`.

### Command-line parameters

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

### Return value

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

### Code that runs before main()

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

### Exceptions

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

