# Complexity

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

