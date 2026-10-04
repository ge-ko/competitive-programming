# Coding Style

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

