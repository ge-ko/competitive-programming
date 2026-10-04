# Graphs

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

## How to store a graph?

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

### Adjacency list

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

### Adjacency matrix

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

## Graph algorithms

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

## Graph traversal algorithms

### Depth-first search (DFS)

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

### Breadth-first search (BFS)

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

## Shortest path algorithms

### Dijkstra

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

### A*

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

## Union-find (aka Disjoint Set Union - DSU)

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

## Minimum Spanning Tree (MST)

An `MST` is a subset of edges that connects all vertices in a *connected*,
*weighted* graph without cycles, with the minimum possible total edge *cost*
(weight).

### Kruskal's algorithm

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

### Prim's algorithm

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

## Topological sort

The topological sort algorithm, given tasks that depend on one another, returns
the tasks in an order such that every task comes after all the tasks it depends
on. This can be represented as a directed graph.

### Kahn's algorithm

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

