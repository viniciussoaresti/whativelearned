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
  - [Nested functions:](#nested-functions)
  - [Double return:](#double-return)
  - [Function order matters! And a lot!](#function-order-matters-and-a-lot)
  - [Multiple code files:](#multiple-code-files)
  - [Namespaces:](#namespaces)
    - [Global namespace:](#global-namespace)
    - [Using namespaces:](#using-namespaces)
  - [Preprocessor:](#preprocessor)
  - [Header Files:](#header-files)
    - [Header Guards:](#header-guards)

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

## Nested functions:

Nested functions like the following example in Javascript:

```js
function doSomething(){
    function doSomethingAgain(){
        console.log('a');
    }
    doSomethingAgain();
}
doSomething();
```

Are not supported in C++. The following code does not compile:

```C++
#include <iostream>

int main()
{
    void foo() // Illegal: this function is nested inside function main()
    {
        std::cout << "foo!\n";
    }

    foo(); // function call to foo()
    return 0;
}//https://www.learncpp.com/cpp-tutorial/introduction-to-functions/
```

## Double return:

I expected that when using double returns both in JS and in C++, they would
generate an error, but that's not the case. This:

```C++
#include <iostream>

int getNumbers()
{
    return 5;
    return 7;
}

int main()
{
    std::cout << getNumbers() << '\n';
    std::cout << getNumbers() << '\n';

    return 0;
}//https://www.learncpp.com/cpp-tutorial/function-return-values-value-returning-functions/
```

Compiles and executes fine, it just ignores the second return statement (and 
everything that could possibly be put after the initial return).

## Function order matters! And a lot!

For example the following code:

```C++
#include <iostream>

int main()
{
    std::cout << "The sum of 3 and 4 is: " << add(3, 4) << '\n';
    return 0;
}

int add(int x, int y)
{
    return x + y;
}//https://www.learncpp.com/cpp-tutorial/forward-declarations/
```

Doesn't compile, generating the error "C3861: 'add': identifier not found".

Since the compiler "compiles the contents of code files sequentially, when the
compiler reaches the function call to add on line 5 of main, it doesn’t know what
add is, because we haven’t defined add until line 9!", 
[Learn CPP](https://www.learncpp.com/cpp-tutorial/forward-declarations/).

This could be "easily" solved by simply reordering the functions, but if we have
a problem where for example a function 'A' uses function 'B' and the reverse is
also true, this wouldn't solve it.

The solution is using what is called a 'forward declaration':

```C++
#include <iostream>

int add(int x, int y); // forward declaration of add() (using a function declaration)

int main()
{
    std::cout << "The sum of 3 and 4 is: " << add(3, 4) << '\n'; // this works because we forward declared add() above
    return 0;
}

int add(int x, int y) // even though the body of add() isn't defined until here
{
    return x + y;
}//https://www.learncpp.com/cpp-tutorial/forward-declarations/
```

## Multiple code files:

The IDE makes the work of linking them together to you, so the following:

```C++
//main.cpp
#include <iostream>

int add(int x, int y); // needed so main.cpp knows that add() is a function defined elsewhere

int main()
{
    std::cout << "The sum of 3 and 4 is: " << add(3, 4) << '\n';
    return 0;
}//https://www.learncpp.com/cpp-tutorial/programs-with-multiple-code-files/
```

```C++
//add.cpp
int add(int x, int y)
{
    return x + y;
}//https://www.learncpp.com/cpp-tutorial/programs-with-multiple-code-files/
```

Works as intended. Just be sure to use the forward declaration.

## Namespaces:

"A namespace is a region that allows you to declare names inside of it for the
purpose of disambiguation. The namespace provides a scope region (called
namespace scope) to the names declared inside of it -- which simply means that
any name declared inside the namespace won’t be mistaken for identical names
in other scopes", [LearnCPP](https://www.learncpp.com/cpp-tutorial/naming-collisions-and-an-introduction-to-namespaces/).

### Global namespace:

"In C++, any name that is not defined inside a class, function, or a namespace
is considered to be part of an implicitly defined namespace called the global
namespace (sometimes also called the global scope)", [LearnCPP](https://www.learncpp.com/cpp-tutorial/naming-collisions-and-an-introduction-to-namespaces/).

Some important details:

```C++
#include <iostream> // handled by preprocessor

// All of the following statements are part of the global namespace
void foo();    // okay: function forward declaration in the global namespace
int x;         // compiles but strongly discouraged: uninitialized variable definition in the global namespace
int y { 5 };   // compiles but discouraged: variable definition with initializer in the global namespace
x = 5;         // compile error: executable statements are not allowed in the global namespace

int main()     // okay: function definition in the global namespace
{
    return 0;
}

void goo();    // okay: another function forward declaration in the global namespace
//https://www.learncpp.com/cpp-tutorial/naming-collisions-and-an-introduction-to-namespaces/
```

### Using namespaces:

We can specify namespaces the way we're usually doing, with the 'scope resolution
operator': `::`.

```C++
std::cout << "Hello world!";
```

We can also use a 'using directive statement':

```C++
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello world!";
    return 0;
}
```

But this is strongly discouraged since even the C++ standards used the standard
namespace to avoid naming conflicts and such.

## Preprocessor:

Before code is compiled, it is preprocessed. This phase of 'translation' doesn't
necessarily understand or parses C++ code, but instead just prepares some stuff
before compilation.

For example, the `#include` directive is read by the preprocessor and it includes
the contents of the specified file.

We can use `#define` to create a macro, but it is generally unsafe to do so.

It is also used to replace occurrences like:

```C++
#include <iostream>

#define MY_NAME "Alex"

int main()
{
    std::cout << "My name is: " << MY_NAME << '\n';

    return 0;
}
```

But this was used in legacy code and is no longer recommended.

There's also `#ifdef, #ifndef, #endif, #if 0` but I don't think they'll be used
frequently. If I change my mind I'll mention them again.

## Header Files:

"Header files allow us to put declarations in one location and then import them
wherever we need them. This can save a lot of typing in multi-file programs",
[LearnCpp](https://www.learncpp.com/cpp-tutorial/header-files/).

They are generally written with the `.h` and `.hpp` extensions, or even without
extensions at all. But `.h` is preferred.

"Header files are often paired with code files, with the header file providing
forward declarations for the corresponding code file. If a header file is paired
with a code file, they should both have the same base name", 
[LearnCpp](https://www.learncpp.com/cpp-tutorial/header-files/).

It's easy to create them through an IDE also.

In order to use it fully, we need to include it into the code file that contains
the functions (it's a best practice) and declarations we need, and also on the
code file we will use them. Example:

```C++
//add.h
int add(int x, int y);
```

```C++
//main.cpp
#include "add.h" // Insert contents of add.h at this point.  
//Note use of double quotes here.
#include <iostream>

int main()
{
    std::cout << "The sum of 3 and 4 is " << add(3, 4) << '\n';
    return 0;
}
```

```C++
//add.cpp
#include "add.h" // Insert contents of add.h at this point.  
//Note use of double quotes here.

int add(int x, int y)
{
    return x + y;
}
```

"Use double quotes to include header files that you’ve written or are expected
to be found in the current directory. Use angled brackets to include headers
that come with your compiler, OS, or third-party libraries you’ve installed
elsewhere on your system", [LearnCpp](https://www.learncpp.com/cpp-tutorial/header-files/).

"When including a header file from the standard library, use the version without
the .h extension if it exists. User-defined headers should still use a .h
extension.

If a header files without a .h extension defines names into the global namespace,
avoid those names, as they may not be available in the global namespace on other
compilers. Prefer the names defined in the std namespace instead.",
[LearnCpp](https://www.learncpp.com/cpp-tutorial/header-files/).

To include header files from other directories, a best practice is to set a
include path or search directory in the IDE project settings.

"Each file should explicitly #include all of the header files it needs to
compile. Do not rely on headers included transitively from other headers", 
[LearnCpp](https://www.learncpp.com/cpp-tutorial/header-files/).

Consider reading the rest of the page mentioned before for additional details.

### Header Guards:

Basically, header guards protect our code from adding the same headers twice,
avoiding duplicate variable and function declarations. For example, if we have
a header that includes the same header that we for some reason include again,
it won't add it twice, generating compilation errors. It's a good practice to
always have header guards.

Example:

```c++
//square.h
#ifndef SQUARE_H
#define SQUARE_H

int getSquareSides()
{
    return 4;
}

#endif

//wave.h
#ifndef WAVE_H
#define WAVE_H

#include "square.h"

#endif

//main.cpp
#include "square.h"
#include "wave.h"

int main()
{
    return 0;
}

//https://www.learncpp.com/cpp-tutorial/header-guards/
```
In modern C++, this can also be achieved with a simpler syntax:

```c++
//square.h
#pragma once

int getSquareSides()
{
    return 4;
}
```

While this is supported by most compilers, "because pragmas are not an official
part of the C++ language (and may not be supported consistently, or at all on
more esoteric platforms), others (such as Google) still recommend sticking
with traditional header guards", [LearnCPP](https://www.learncpp.com/cpp-tutorial/header-guards/).