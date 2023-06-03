# C++

"C++ (pronounced see plus plus) was developed by Bjarne Stroustrup at Bell Labs as an extension to C, starting in 1979. C++ adds many new features to the C language, and is perhaps best thought of as a superset of C, though this is not strictly true (as C99 introduced a few features that do not exist in C++). C++’s claim to fame results primarily from the fact that it is an object-oriented language", [Learn CPP](https://www.learncpp.com/cpp-tutorial/introduction-to-cplusplus/).

# Contents:

- [C++](#c)
- [Contents:](#contents)
- [Hello world:](#hello-world)
- [Concepts:](#concepts)
  - [Comments:](#comments)
  - [Variables initialization:](#variables-initialization)
  - [Maybe unused:](#maybe-unused)

# Hello world:

```c++
#include <iostream>

int main()
{
   std::cout << "Hello world!";
   return 0;
}
```

# Concepts:

## Comments:

The same as usual: `//` and `/* */`.

## Variables initialization:

Copy initialization (`int a = 5;`) was sometimes not used and direct initialization (`int a(5);`) was preferred for
performance reasons. But it has "generally fallen out of favor in modern C++", [Learn CPP](https://www.learncpp.com/cpp-tutorial/variable-assignment-and-initialization/). Now the go-to is list initialization, that can attribute one or multiple values
(`int width { 5 };` or `int width = { 5 };`).

## Maybe unused:

Sometimes a variable is not used and causes a warning (or even an error if the compiler is configured that way), and we
can (if we really aren't gonna use it but still want to declare it) do something like this to avoid it:

```c++
int main()
{
    [[maybe_unused]] int x { 5 };

    // since x is [[maybe_unused]], no warning generated

    return 0;
} //https://www.learncpp.com/cpp-tutorial/variable-assignment-and-initialization/
```