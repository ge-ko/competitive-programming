# Competitive Programming

I'm creating this repo to provide my son Alex with the basic knowledge to
bootstrap his endeavor in [competitive
programming](https://en.wikipedia.org/wiki/Competitive_programming).

In 2023/2024 he [ranked
10th](https://soi.ch/contests/2024/round1/ranking-junior/) in the junior group
in the first round of the Swiss Olympiad in Informatics.

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
[Pascal](<https://en.wikipedia.org/wiki/Pascal_(programming_language)>).

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

To get interactive input use `cin` (_see-in_, from character input). It will
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

You can run the same program that is using files with terminal IO by just
setting `in` and `out` to be `cin` and `cout` instead of files.

```c++
istream in(cin.rdbuf());
ostream out(cout.rdbuf());
// ifstream in("input.txt");
// ofstream out("output.txt");
```

You can mix file and terminal IO. You can also use the special output for errors
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
variables as a _name_ by which we refer to an address in the memory.

Every variable has a _data type_. The
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
depends on one or more variables. Very often it is one variable called `n`.

The program complexity shows how the time and space (or memory) used by the
program correspond to the input size.

```c++
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
    vector<int> bits;
    for (int i = n; i > 0; i /= 2)
        bits.push_back(i % 2);
    return bits;
}

// O(sqrt n) - fractional time and space
// Grows as fast as square root of n
// Example: Find the divisors of a number
vector<int> divisors(int n)
{
    vector<int> divisors;
    int sqrt_n = sqrt(n);
    for (int i = 1; i <= sqrt_n; ++i)
    {
        if (n % i == 0)                     // if i is a divisor of n
        {
            if (i * i == n)                 // if n is a perfect square
            {
                divisors.push_back(i);      // sqrt_n is a devisor with no counterpart
            }
            else                            // all other divisors come in paors
            {
                divisors.push_back(i);
                divisors.push_back(n/i);
            }
        }
    }
    return divisors;
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
    for (int i = 0; i < v.size(); ++i)
        for(int j = 1; j < v.size() - i; ++j)
            if (v[j-1] > v[j])
                swap(v[j-1], v[j]);
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
                r[i][j] += a[i][k] * b [k][j];
        }
    return r;
}

// O(2^n) - exponential time and space
// Grows as fast as 2^n
// Example: Find all subsets of a vector
vector<vector<int>> powerset(const vector<int>& v)
{
    vector<vector<int>> powerset;
    powerset.push_back(vector<int>());      // start with the empty set

    for (auto e : v)                        // for each element in v
    {
        vector<vector<int>> copy = powerset;// copy all subsets so far
        for (auto s : copy)
        {
            s.push_back(e);                 // append the element to each subset
            powerset.push_back(s);          // append the subsets to the powerset
        }
    }
    return powerset;
}

// O(n!) - factorial time and space
// Grows as fast as n!
// Example: Find all permutations of a string
vector<vector<int>> permutations(vector<int>& v)
{
    vector<vector<int>> permutations;
    permutations.push_back(v);

    while (std::next_permutation(v.begin(), v.end()))
    {
        permutations.push_back(v);
    }
    return permutations;
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

Modern processors run at 4 GH clock speed. They can execute 4 billion operations
in a second. The runtime of an `O(n)` algorithm for `n <= 2^32` will be few
seconds which is acceptable. However, for `n <= 2^64`, the runtime will be
roughly 100 years.

Choose the right algorithm for the input constraints of the problem.

| input size   | complexity     | examples              |
| ------------ | -------------- | --------------------- |
| n <= 11      | O(n!)          | Permutations          |
| n <= 32      | O(2^n)         | Power set             |
| n <= 10^3    | O(n^3)         | Matrix multiplication |
| n <= 5\*10^4 | O(n^2)         | Bubble sort           |
| n <= 10^6    | O(n log n)     | Merge sort            |
| n <= 10^9    | O(n)           | Maximum subarray      |
| n <= 10^18   | O(sqrt n)      | Divisors              |
| n > 10^18    | O(log n), O(1) | Binary search         |

## Graphs

(source <https://soi.ch/wiki/graphs/>)

A graph is a set of points and connections between those points. A point is
usually called a _node_ or _vertex_, and for a connection, we use the term
_edge_.

Nodes are usually numbered form `1` to `n`. For simplicity we assume here that
nodes are numbered from `0` to `n-1`. If that is not the case, adjust numbering
by adding/subtracting `1` or by skipping the `0` node.

Two nodes are _adjacent_ or _neighbors_ if they are connected through an edge.
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

There are two common ways to store graphs in memory: _adjacency list_ and
_adjacency matrix_. They have different space and time tradeoffs.

| space / time               | adjacency list | adjacency matrix |
| -------------------------- | -------------- | ---------------- |
| storage                    | O(n+m)         | O(n^2)           |
| insert edge                | O(1)           | O(1)             |
| delete edge                | O(m)           | O(1)             |
| check if edge exists       | O(m)           | O(1)             |
| find all edges from a node | O(m)           | O(n)             |
| traverse graph (BFS/DFS)   | O(n+m)         | O(n^2)           |

#### Adjacency list

The most common way to store a graph is a so-called _adjacency list_. For every
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

To print a graph, overload ostream::operator<<.

```c++
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
    for (int i = 0; i < g.size(); ++i)
    {
        os << i << ": " << g[i] << '\n';
    }
    return os;
}

int main()
{
    ...

    cout << g;  // prints to whole graph
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

In _adjacency matrix_ rows and columns represent the nodes and the cell at row
`a` and column `b` represents the edge between node `a` and node `b`. You can
either use `bool` to encode the presence or absence of an edge between `a` and
`b` or `int` to encode a weight of the edge between `a` and `b`.

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

-   the node attached to the last visited node (DFS)
-   the node with the least number of edges from the start (BFS)
-   the node with the shortest path from the start (Dijkstra)
-   the node that has the shortest distance _by air_ from the start (A\*)

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

### Graph traversal algorithms

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

### Shortest path algorithms

#### Dijkstra

Dijkstra is a traversal algorithm that uses a `priority_queue` the find the
shortest path from a start to all connected nodes or to a specific finish node.

Google maps uses Dijkstra algorithm to show shortest distance between source and
destination.

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

#### A\*

### Union-find (aka Disjoint Set Union - DSU)

_Union-find_ is a data structure that helps manage a collection of disjoint sets.
It does that by associating each component of the graph with a representative node (aka _chef_) and
checking if two nodes belong to the same component.

_Union-find_ has two operations:

-   `find` - finds the _chef_ of a node
-   `unite` - creates a union between two components

```c++
using node = int;

struct ufind
{
    // holds the chef of a non-chef node,
    // or -size of the component for chef nodes
    vector<node> c;
    // each node is a component of size 1 (stored as -1)
    ufind(int n) : c(n, -1) {}

    int find(node k)
    {
        return c[k] < 0 ? k : c[k] = find(c[k]);
    }

    void unite(node a, node b)
    {
        a = find(a); b = find(b);
        if (a == b) return; // a and b in same component
        if (c[a] > c[b]) swap(a, b);
        c[a] += c[b];
        c[b] = a;
    }
};
```

### Minimum Spanning Tree (MST)

An `MST` is a subset of edges that connects all vertices in a _connected_, _weighted_ graph without cycles, with the minimum possible total edge _cost_ (weight).

#### Kruskal's algorithm

Kruskal's algorithm is a greedy algorithm, which sorts the edges by _cost_ and checks for each edge if realized whether a cycle is created. It does that by using _Union-Find_.

```c++
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

Prim's algorithm is very similar to `Dijkstra's`. It uses a priority queue to sort all edges when pushed into it. Each edge in the queue gets added to the mst only if the node the edge leads to has never been visited before. Afterwards we take that node's neighboring edges and we push them to the queue.

```c++
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
    for(auto& o : g[0]) pq.push(o);

    while(!pq.empty())
    {
        edge i = pq.top();
        node v = i.second.second;
        pq.pop();

        if (visited[v]) continue;
        visited[v] = true;

        mst.push_back(i);

        for(auto& o : g[v]) pq.push(o);
    }
    return mst;
}
```

### Topological sort

Topological sort algorithm, when given tasks, some of which dependent on others,
returns the tasks in order, such that all can be completed after the ones they
are dependent on. This can be represented as a directed graph.

#### Kahn's algorithm

Kahn's algorithm does a topological sort by setting an `indegree` for each node
(number of nodes pointing at that node). After that it pushes into a queue only
the nodes with `indegree = 0` (they don't depend on other nodes). Then it cycles
through the queue and puts each node it goes through in a vector that stores the
topological orientation. Finally for each node in the queue it takes its
neighboring nodes, decrements their `indegree` and pushes all nodes with
`indegree = 0` to the queue.

```c++
using node = int;
using neighbors = vector<node>;
using graph = vector<neighbors>;

vector<node> kahn(const graph& g)
{
    int n = g.size();
    vector<int> indegree(n, 0);
    //sets indegree for each node
    for (node u = 0; u < n; ++u)
        for (auto v : g[u])
        ++indegree[v];

    queue<node> q;
    //pushes all nodes with indegree = 0
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
        //pushes all nodes with new indegree = 0;
        if (indegree[v] == 0) q.push(v);
        }
    }

    // checks for cycle
    return toposort.size() == n ? toposort : vector<node>{};
}

```

## TODO

The next sections are not complete

### Install and configure Visual Studio Code

Follow [these](https://code.visualstudio.com/docs/introvideos/basics)
instructions to install, configure Visual Studio Code and start using it.

Install the [SOI Code](https://soi.ch/wiki/soi-vscode/) extension.

Create `bits/stdc++.h` is instructed
[here](https://github.com/khaveesh/macOS-stdc.h).

### Install CLion

If I manage to obtain free licence, I will include instructions to install and
use CLion.

### Call-by-value or call-by-reference

-   Explain pointer type
-   Explain reference type
-   Explain what is a side effect
-   Explain call-by-value and call-by-reference
-   Explain the [best
    practice](https://www.stroustrup.com/bs_faq2.html#call-by-reference):

Best practice:

-   To have a side effect call by reference or use a pointer; e.g. `void
f(type&);` or `void f(type*);`
-   No side effect but the parameter is big, call by const reference; e.g. `void
f(const type&);`
-   Otherwise, call by value; e.g. void f(type);

### Change the C++ version

repl.it vscode <https://replit.com/@GeorgiKostov/cppver>

### Terminal

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
