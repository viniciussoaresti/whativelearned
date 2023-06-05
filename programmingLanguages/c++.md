# C++

"C++ (pronounced see plus plus) was developed by Bjarne Stroustrup at Bell Labs
as an extension to C, starting in 1979. C++ adds many new features to the C
language, and is perhaps best thought of as a superset of C, though this is
not strictly true (as C99 introduced a few features that do not exist in C++).
C++’s claim to fame results primarily from the fact that it is an object-oriented
language", [Learn CPP](https://www.learncpp.com/cpp-tutorial/introduction-to-cplusplus/).

# Contents:

- [C++](#c)
- [Contents:](#contents)
- [Hello world:](#hello-world)
- [Concepts:](#concepts)
  - [Comments:](#comments)
  - [Variables initialization:](#variables-initialization)
  - [Maybe unused:](#maybe-unused)
  - [Input/output library](#inputoutput-library)
    - [std::cout:](#stdcout)
    - [std::cin:](#stdcin)

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

Copy initialization (`int a = 5;`) was sometimes not used and direct initialization
(`int a(5);`) was preferred for performance reasons. But it has "generally fallen
out of favor in modern C++",
[Learn CPP](https://www.learncpp.com/cpp-tutorial/variable-assignment-and-initialization/).
Now the go-to is list initialization, that can attribute one or multiple values
(`int width { 5 };` or `int width = { 5 };`).

## Maybe unused:

Sometimes a variable is not used and causes a warning (or even an error if the
compiler is configured that way), and we can (if we really aren't gonna use it
but still want to declare it) do something like this to avoid it:

```c++
int main()
{
    [[maybe_unused]] int x { 5 };

    // since x is [[maybe_unused]], no warning generated

    return 0;
} //https://www.learncpp.com/cpp-tutorial/variable-assignment-and-initialization/
```

## Input/output library

"The input/output library (io library) is part of the C++ standard library that
deals with basic input and output. We’ll use the functionality in this library
to get input from the keyboard and output data to the console. The io part of
iostream stands for input/output",
[Learn CPP](https://www.learncpp.com/cpp-tutorial/introduction-to-iostream-cout-cin-and-endl/).

```c++
#include <iostream>
```

### std::cout:

```c++
#include <iostream>

int main()
{
    std::cout << "Hello world!";
    return 0;
}
```

Here's when things start to be a little different than some languages like Java,
C# and Javascript. When coding on them, you can concatenate strings easily doing
something like: `"1" + "2"`. But in C++, this occurs in an error, informing us
that we can't sum two pointers. To solve this, we can utilize the insertion
operator (<<) again to concatenate:

```c++
#include <iostream>

int main()
{
    std::cout << "Hello" << " world!";
    return 0;
}
```

In order to print multiple lines, we can use `\n` as usual on the strings, or use
`std::endl`. As for the difference between the two approaches, it seems like they
are the same, but `std::endl` flushes the output buffer, meaning that, by using it,
it forces the output buffer to print the content, instead of accumulating, which
can occur. So, it's a good practice to utilize `endl` at the end of the outputs,
if we need to ensure the text is displayed. The input and output streams are
synchronized, so, when waiting for the user to input something, the output buffer
is also flushed by default.

In summary:

Doing this:

```c++
std::cout << "Endl in C++" << std::endl;
```

Is equivalent to:

```c++
std::cout << "Endl in C++" << "\n" << std::flush;
```

So, `\n` is faster in turn, because it only realizes one function call.

More details [here](https://www.scaler.com/topics/endl-in-cpp/).

### std::cin:

```c++
#include <iostream>  // for std::cout and std::cin

int main()
{
    std::cout << "Enter a number: "; // ask user for a number

    int x{ }; // define variable x to hold user input (and zero-initialize it)
    std::cin >> x; // get number from keyboard and store it in variable x

    std::cout << "You entered " << x << '\n';
    return 0;
} //https://www.learncpp.com/cpp-tutorial/introduction-to-iostream-cout-cin-and-endl/
```

Using double variables:

```c++
#include <iostream>  // for std::cout and std::cin

int main()
{
    std::cout << "Enter two numbers separated by a space: ";

    int x{ }; // define variable x to hold user input (and zero-initialize it)
    int y{ }; // define variable y to hold user input (and zero-initialize it)
    std::cin >> x >> y; // get two numbers and store in variable x and y respectively

    std::cout << "You entered " << x << " and " << y << '\n';

    return 0;
}//https://www.learncpp.com/cpp-tutorial/introduction-to-iostream-cout-cin-and-endl/
```