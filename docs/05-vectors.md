# Vectors

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

