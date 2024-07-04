# Competitive Programming

I'm creating this repo to provide my son Alex with the basic knowledge to
bootstrap his endeavor in [competitive
programming](https://en.wikipedia.org/wiki/Competitive_programming).

## Start coding

Start solving problems in [HackerRank](https://www.hackerrank.com/). HackerRank
provides a code editor, compiler (choose C++14) and a bunch of algorithmic
problems to solve.

To solve a problem that is not on HackerRank, use [repl.it](https://repl.it/).

### Program skeleton

Use this skeleton code to start coding. Put your code in place of the `|`
symbol. Name the file `main.cpp`.

```c++
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
all other header files of the C++ Standard Library through `#include
<bits/stdc++.h>`.

You can find a complete reference to the C++ Language and the C++ Standard
Library at [cppreference.com](https://cppreference.com/).

To avoid clashes of functions with the same name in different libraries, C++
provides namespaces. The C++ Standard Library is in the `std` namespace . In
competitive programs it is convenient to have the statement `using namespace
std;` so that all functions can be used directly without the need to prefix them
with `std::`.

In competitive programs you need to input/output data from/to the console as
fast as possible. It's advisable to put the `ios_base::sync_with_stdio(false);`
and `cin.tie(0);` in the beginning of your main function.

### Coding style

Style refers to the way you organize your code so that it can be read and
understood. The style is a matter of personal taste.
[Consistency](https://www.stroustrup.com/bs_faq2.html#layout-style) in using the
same style throughput the program is more important then the specific style you
choose. I encourage you to form your own style.

[Indentation](https://en.wikipedia.org/wiki/Indentation_style) is very
important. I personally prefer 4 spaces indentation. 4 spaces are enough to
visually separate the body and not too much to quickly run out of screen space.

Using spaces is better than tab as tabs may be visualized as 4 or 8 spaces and
if mixed with spaces will cause the code to look ugly.

I prefer the
[Allman](https://en.wikipedia.org/wiki/Indentation_style#Allman_style) style as
it clearly separates control statements from the body and perhaps because the
first programming language is studied was
[Pascal](https://en.wikipedia.org/wiki/Pascal_(programming_language)).

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

As any true C++ developer, I avoid using capital letters. To name variables, I
use [snake_case](https://en.wikipedia.org/wiki/Snake_case).

### Computer

Computers are machines that execute algorithms (aka instructions, programs or
code) over data. There are many computer architectures with the most popular
being the [von Neumann
architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture). It keeps
the code and the data in the same
[memory](https://en.wikipedia.org/wiki/Computer_memory) and has a [Central
Processing Unit (CPU)](https://en.wikipedia.org/wiki/Central_processing_unit)
that executed the code over the data. The memory itself exchanges code and data
with the slower but durable [mass
storage](https://en.wikipedia.org/wiki/Mass_storage) trough the Input and
Output.

### Input and output

Your program needs to get input from the user and provide them with an output.
Input and output (IO) can be provided interactively through the
[terminal](https://en.wikipedia.org/wiki/Computer_terminal) or provided in a
batch through files.

To get interactive input use `cin` (*see-in*, from character input). It will
convert the characters to the respective type of the variables. It will skip
through spaces and new lines to get the next variable.

```c++
int t, n; cin >> t >> n;
```

To provide interactive output, use `cout`. Don't forget to put a new line `'\n'`
wherever needed. You can also use `endl` for a new line but it takes more time
to execute and is better avoided in competitive programming.

```c++
cout << "t = " << t
     << "\nn = " << n
     << '\n';
cout << endl;
```

To replace interactive IO with batch IO, use files. Create the input file in
advance and fill it in with data. The output file will be created automatically.
The output will be overwritten on every execution of the program.

```c++
ifstream in("input.txt");
ofstream out("output.txt");
```

You can have the same program using the terminal and files by just replacing
`in` and `out` to be `cin` and `cout` instead of files.

```c++
istream in(cin.rdbuf());
ostream out(cout.rdbuf());
// ifstream in("input.txt");
// ofstream out("output.txt");
```

You can mix file in terminal IO. You can also use the special output for errors
`cerr`.

IO has a long history. It started with [punched
cards](https://en.wikipedia.org/wiki/Punched_card) for the input of data and
programs, and [dot matrix
printers](https://en.wikipedia.org/wiki/Dot_matrix_printer) for the output of
the program. Files were stored on [hard
disks](https://en.wikipedia.org/wiki/Hard_disk_drive) and [magnet
tapes](https://en.wikipedia.org/wiki/Magnetic-tape_data_storage).
[Terminals](https://en.wikipedia.org/wiki/Computer_terminal) introduced the
[keyboard](https://en.wikipedia.org/wiki/Computer_keyboard) and the text-based
[monitor](https://en.wikipedia.org/wiki/Computer_monitor). [Floppy
disks](https://en.wikipedia.org/wiki/Floppy_disk) and [flash
drives](https://en.wikipedia.org/wiki/USB_flash_drive) made it possible to move
data between computers.
[GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) introduced the
graphical monitor and the [pointing
device](https://en.wikipedia.org/wiki/Pointing_device) (like the mouse).
[Networks](https://en.wikipedia.org/wiki/Computer_network) made it even more
easy to move data between computers.

Text-based IO through the terminal and files are commonly used in competitive
programming. GUI and networks are not used.

### Variable declaration and initialization

In C++ you can store data in the memory by using variables. You can think of
variables as a *name* by which we refer to an address in the memory.

Every variable has a *data type*. The
[type](https://en.cppreference.com/w/cpp/language/types) determines how much
memory it uses (measured in bytes) and what types of operations can be performed
on the data (addition, multiplication, etc).

```c++
int i;      // -2*10^9 < i < 2*10^9
long j;     // -9*10^18 < j < 9*10^18
bool b;     // b is true and false
string s;   // strings of characters, like "abc"
```

Often you will need to choose the type based on the input size. If a number is
less than a billion, choose `int`. If you need to multiply two `int`s or sum a
billion of `int`s, choose `long`. Since numbers are stored in binary format,
knowing some of the powers of 2 is very useful.

```text
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
2^16 =          65,536  = 2 bytes = wchar (can fit Unicode character)
...
2^20                    = 1 Mb >= 10^6
2^24 =      16,777,216  = 3 bytes = RGB
...
2^30                    = 1 Gb >= 10^9
2^31 =   2,147,483,647  = int
2^32 =   4,294,967,295  = 4 bytes = unsigned int
...
2^40                    = 1 Tb >= 10^12
...
2^50                    = 1 Pb >= 10^15
...
2^60                    = 1 Eb >= 10^18
...
2^63                    = long
2^64                    = 4 bytes = unsigned long
...
2^305                   >= 10^90 >= the information capacity of the universe
```

In order to use a variable it first needs to be defined. It's a good practice to
define the variable as close as possible to where it is used. Variables can be
defined even in loops. They will use the same memory in every iteration of the
loop.

```c++
int i = 10;
while (i--)
{
    int j = i * i;
    cout << j << '\n';
}
```

Unless initialized, variables contain random data. It's a good practice to
immediately initialize every variable after it is defined.

```c++
int i = 0;
int n; cin >> n;
for (int i = 0; i < 10; cout << ++i);
```

### Vector

Vectors are multiple variables stored contiguously in the memory. Each variable
in the vector has in index starting at 0.

```c++
vector<int> a(10);                      // a vector of 10 elements of type int
for (int i = 0; i < a.size(); ++i)      // a.size() is 10
{
    a[i] = i + 1;                       // assign the i-th element of the vector
}
a.push_back(11);                        // add another element to the back
a.push_back(12);                        // and another one
cout << a[0] + a[4] + a[11] << '\n';    // 18 = 1st + 5th + 12th elements
```

## Complexity

Programs have certain input. The size of the input may vary. Usually the size
depends on one or more variables.  Very often it is one variable called `n`.

The program complexity shows how the time and space (or memory) used by the
program correspond to the input size.

```c++
int n; cin >> n;

// O(1) - constant time and space
// does not grow with n
int a = 42;
cout << a << '\n';

// O(log n) - logarithmic time and space
// grows as fast as the base-2 logarithm of n
vector<int> bits;
for (int i = n; i > 0; i /= 2)
    bits.push_back(i % 2);
for (auto bit : bits)
    cout << bit;
cout << '\n';

// O(n) - linear time and space
// grows as fast as n
vector<int> v(n);
for (int i = 0; i < n; ++i)
    cin >> v[i];

// O(n^2) - quadratic time and space
// grows as fast as n^2
vector<vector<int>> m(n, vector<int>(n));
for (int i = 0; i < n; ++i)
    for (int j = 0; j < n; ++j)
        cin >> v[i][j];

// O(2^n) - exponential time and space
// grows as fast as 2^n
vector<vector<int> powerset;            // to store all subsets of the vector v
powerset.push_back(vector<int>());      // start with the empty set

for (auto e : v)                        // for each element in v
{
    vector<vector<int> copy = powerset; // copy all subsets so far
    for (auto s : copy)
    {
        s.push_back(e);                 // append the element to each subset
        powerset.push_back(s);          // append the subsets to the powerset
    }
}
```

## Graphs

(source <https://soi.ch/wiki/graphs/>)

A graph is a set of points and connections between those points. A point is
usually called a *node* or *vertex*, and for a connection, we use the term
*edge*.

Nodes are usually numbered form `1` to `n`. For simplicity we assume here that
nodes are numbered from `0` to `n-1`. If that is not the case, adjust numbering
by adding/subtracting `1` or by skipping the `0` node.

Two nodes are *adjacent* or *neighbors* if they are connected through an edge.
Not every two nodes need to be connected.

Graphs can be directed or undirected. Undirected graphs have a bi-directional
connection between every two nodes. Directed graphs may have one-way connections
between nodes.

A path between two nodes is a list of unique nodes (including the two nodes)
such that all the nodes in the path are connected. If there is no path between
two nodes, they belong to different connected components. If a path exists form
a node to itself, there is a cycle in the graph.

A tree is an acyclic connected graph. A forest is an acyclic graph.

Edges may have an associated weight that can be used to describe things like
length of roads, price of airplane tickets, etc.

### How to store a graph?

There are two common ways to store graphs in memory: *adjacency list* and
*adjacency matrix*. They have different space and time tradeoffs.

| space / time               | adjacency list | adjacency matrix |
|----------------------------|----------------|------------------|
| storage                    | O(n+m)         | O(n^2)           |
| insert edge                | O(1)           | O(1)             |
| delete edge                | O(m)           | O(1)             |
| check if edge exists       | O(m)           | O(1)             |
| find all edges from a node | O(m)           | O(n)             |
| traverse graph (BFS/DFS)   | O(n+m)         | O(n^2)           |

#### Adjacency list

The most common way to store a graph is a so-called *adjacency list*. For every
node you store a list of all of its neighbors. If the graph is undirected, for
each connected pair fo nodes `a` and `b` store two directed edges from `a` to
`b` and from `b` to `a`.

```c++
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

If you need to store edge wights, use a `pair`.

```c++
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

In *adjacency matrix* rows and columns represent the nodes and the cell at row
`a` and column `b` represents the edge between node `a` and node `b`. You can
either use `bool` to encode the presence or absence of an edge between  `a` and
`b` or `int` to encode a weight of the edge between  `a` and `b`.

```c++
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

* the node attached to the last visited node (DFS)
* the node with the least number of edges from the start (BFS)
* the node with the shortest path from the start (Dijkstra)
* the node that has teh shortest distance *by air* from the start (A*)

Graph algorithms have a common structure.

```c++
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

#### Depth-first search (DFS)

Depth-first search (DFS) is a traversal algorithm that uses a `stack`.

```c++
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

The algorithm can also use the call stack to store next elements to visit.

```c++
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
        dfs(g, u, visited, path);   // push u to call stack and call recursively
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

#### Breadth-fist search (BFS)

Breadth-fist search (BFS) is a traversal algorithm that uses a `queue`.

```c++
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> dfs(const graph& g)
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

#### Dijkstra

Dijkstra is a traversal algorithm that uses a `priority_queue` the find the
shortest path from a start to all connected nodes or to a specific finish node.

Google maps uses Dijkstra algorithm to show shortest distance between source and destination.

```c++
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

    priority_queue<edge> pq;
    pq.push(make_pair(0, start));

    while (!pq.empty())
    {
        node v = pq.top().second;   // the node with shortest path from start
        pq.pop();

        if (visited[v]) continue;

        // visit
        visited[v] = true;
        path.push_back(v);

        if (v == finish) break;     // remove this to traverse the whole graph

        for (edge e : g[v])
        {
            weight w = e.first;
            node u = e.second;
            if (dist[u] <= dist[v] + w) continue;   // this path to u is worse

            dist[u] = dist[v] + w;
            pq.push(make_pair(-dist[u], u));
        }
    }

    return path;
}
```

## TODO

#### A*

#### Topological sort

The next sections are not complete

## Install and configure Visual Studio Code

Follow [these](https://code.visualstudio.com/docs/introvideos/basics)
instructions to install, configure Visual Studio Code and start using it.

Install the [SOI Code](https://soi.ch/wiki/soi-vscode/) extension.

Create `bits/stdc++.h` is instructed
[here](https://github.com/khaveesh/macOS-stdc.h).

## Call-by-value or call-by-reference

Explain pointer type Explain reference type Explain what side effect is Explain
call-by-value and call-by-reference Explain the [best
practice](https://www.stroustrup.com/bs_faq2.html#call-by-reference):

* To have a side effect call by reference or use a pointer; e.g. void f(type&);
  or void f(type*);
* No side effect but the parameter is big, call by const reference; e.g. void
  f(const type&);
* Otherwise, call by value; e.g. void f(type);

## Change the C++ version

repl.it vscode <https://replit.com/@GeorgiKostov/cppver>

## Terminal

parameters, return value, cin, cout, cerr.

Provide more details on passing parameters to your program, getting a return
value from your program, executing code even before `main()`, exceptions and
many more.

```c++
#define all(c) (c).begin(), (c).end()
```

All algorithms in the C++ Standard Library which iterate over data structures
accept a pair of begin and end iterators. In competitive programs it is
convenient to replace that code with just `all()`. That's why we need to define
this macro: `#define all(c) (c).begin(), (c).end()`.
