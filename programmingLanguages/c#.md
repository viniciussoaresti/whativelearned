# C#

"C# is a modern, object-oriented, component-oriented and type-safe programming language, and it provides language constructs to directly support these concepts, making C# a natural language in which to create and use software components. Since its origin, it has added features to support new workloads and emerging software design practices, enabling developers to build many types of secure and robust applications that run in the .NET ecosystem. C# has its roots in the C family of languages and will be immediately familiar to C, C++, Java, and JavaScript programmers", [Microsoft on C#](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/).

# Contents:

- [C#](#c)
- [Contents:](#contents)
  - [Concepts:](#concepts)
    - [C# and .NET:](#c-and-net)
    - [Classes:](#classes)
    - [Namespaces:](#namespaces)
    - [Assembly:](#assembly)
    - [Hello World and Importing Classes from Namespaces:](#hello-world-and-importing-classes-from-namespaces)
    - [Project Layout:](#project-layout)
      - [Properties:](#properties)
      - [References:](#references)
      - [App.config:](#appconfig)
      - [Program.cs:](#programcs)
    - [Variables and Types:](#variables-and-types)
    - [Nuget:](#nuget)
    - [Structs:](#structs)
    - [Inheritance in C#:](#inheritance-in-c)
    - [Overriding methods in C#:](#overriding-methods-in-c)
    - [Sealed classes in C#:](#sealed-classes-in-c)
  - [Tips:](#tips)
    - [Getters and setters:](#getters-and-setters)
    - [Tests](#tests)
    - [Type conversion:](#type-conversion)
    - [Visual Studio shortcuts:](#visual-studio-shortcuts)
      - [Prop:](#prop)

## Concepts:

### C# and .NET:

C# is a programming language, whereas .NET is a framework for building applications on Windows. For example, F# can be used with .NET.

.NET basically consists of two components, the Common Language Runtime (CLR) and the Class Library (all classes available through .NET).

For the CLR, C# is similar to Java, and translates the code to the Common Intermediate Language (CIL), more or less what in Java is called ByteCode. Then, compared to Java where the ByteCode is interpreted by the JVM, the IL Code is interpreted by the CLR. The latter process utilizes a just-in-time compiler (JIT) to turn it into machine code.

There's a lot of .NET terms to get to know:

First, **.NET** (no add-ons), is an open-source, cross-platform framework. It came to life after .NET Core.

The .NET **Core** framework is an implementation of the .NET framework designed to be cross-platform, and it's more used in server applications, as the GUI provided in base .NET projects, and some specific functionalities (like WMI) are not available.

There's the .NET **Framework**, which is a framework for building applications specifically on Windows, providing access to features available only on this OS, and **Xamarin/Mono**, that is for building applications across different mobile OS's.

### Classes:

Classes are containers that hold data (attributes) and methods (functions). All that is contained in a class is considered a "member".

### Namespaces:

Namespaces are containers of related classes.

### Assembly:

Assemblies are containers of related namespaces. Physically, a file on the disk, as an DLL (Dynamically Linked Library) or executable file. So, an complete application can consist of one or many assemblies bundled together, depending on how the app's structured.

### Hello World and Importing Classes from Namespaces:

```C#
using System;

namespace HelloWorld {
    class Program {
        static void Main(string[] args){
            Console.WriteLine("Hello World!");
        }
    }
}
```

Here we see the namespace, where we're able to access all classes within it.

The 'using' keyword, as you could infer, is basically an import of another namespace, so you're able to use another namespace's classes. We can use the imported classes by just calling them, or by using the complete notation, such as:

```C#
System.Console.WriteLine("Hello World!");
```

### Project Layout:

Under a "Solution", there will exist one or many more projects, each with the following layout:

#### Properties:

A folder that has the `AssemblyInfo.cs` file. This is the info that will be used to mount the assembly that will be produced as a result of the compilation, like version, name, etc.

#### References:

Any assemblies that are referenced in the project, on an basic example, part of the .NET framework.

#### App.config:

An XML file that contains configuration data for the project, as the .NET framework version, connection to the database, etc.

#### Program.cs:

The program/code itself.

### Variables and Types:

![Primitives](./cSharpAssets/primitives.png?raw=true)

(Programming with Mosh)

### Nuget:

"NuGet is the package manager for .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers", [Nuget](https://www.nuget.org/).

### Structs:

"Structs are similar to classes in that they represent data structures that can contain data members and function members. However, unlike classes, structs are value types and do not require heap allocation. A variable of a struct type directly contains the data of the struct, whereas a variable of a class type contains a reference to the data, the latter known as an object.

Structs are particularly useful for small data structures that have value semantics. Complex numbers, points in a coordinate system, or key-value pairs in a dictionary are all good examples of structs", [C# Reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/language-specification/structs).

### Inheritance in C#:

To use inheritance in C#, we use the ':' notation:

```c#
namespace namespace
{
    public class Class2 : Class1{ //Class 2 is child of Class 1
        //Other Properties
    }
}
```

### Overriding methods in C#:

To use methods overriding in C#, we use the 'override' notation:

```c#
namespace namespace
{
    public class Class2 : Class1{ //Class 2 is child of Class 1
        public override MethodName(){
            Console.WriteLine("Override!");
        }
    }
}
```

### Sealed classes in C#:

"When applied to a class, the sealed modifier prevents other classes from inheriting from it.

You can also use the sealed modifier on a method or property that overrides a virtual method or property in a base class. This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties", [C# Reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/sealed). Example:

```c#
class A {}
sealed class B : A {} //no other class can inherit B

//and

class X
{
    protected virtual void F() { Console.WriteLine("X.F"); }
    protected virtual void F2() { Console.WriteLine("X.F2"); }
}

class Y : X
{
    sealed protected override void F() { Console.WriteLine("Y.F"); }
    protected override void F2() { Console.WriteLine("Y.F2"); }
}

class Z : Y
{
    // Attempting to override F causes compiler error CS0239.
    // protected override void F() { Console.WriteLine("Z.F"); }

    // Overriding F2 is allowed.
    protected override void F2() { Console.WriteLine("Z.F2"); }
}
```

## Tips:

### Getters and setters:

With C# you can simplify basic getters and setters for an private field.

"In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors. They also enable client code to create objects. When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's get and set accessors. In C# 9 and later, init accessors can also be declared as auto-implemented properties", [C# Auto-Implemented Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

```c#
// This class is mutable. Its data can be modified from
// outside the class.
class Customer
{
    // Auto-implemented properties for trivial get and set
    public double TotalPurchases { get; set; }
    public string Name { get; set; }
    public int CustomerId { get; set; }

    // Constructor
    public Customer(double purchases, string name, int id)
    {
        TotalPurchases = purchases;
        Name = name;
        CustomerId = id;
    }

    // Methods
    public string GetContactInfo() { return "ContactInfo"; }
    public string GetTransactionHistory() { return "History"; }

    // .. Additional methods, events, etc.
}

class Program
{
    static void Main()
    {
        // Intialize a new object.
        Customer cust1 = new Customer(4987.63, "Northwind", 90108);

        // Modify a property.
        cust1.TotalPurchases += 499.99;
    }
}
```

Or you can use the specific way of declaring it when needed:

```C#
public int Salary  
{  
    get  
    {  
        return _salary;  
    }  
    set  
    {  
        _salary = value;  
    }  
} 
```

### Tests

With Visual Studio, you can automatically create unit tests right-clicking the class you'd like to test. So we'll get something like this:

```c#
[TestMethod()]
public void SomaTest()
{
var a = 1;
var b = 1;
var testClass = new Class1();
var result = testClass.Soma(a, b);
Assert.AreEqual(a+b, result);
}
```
### Type conversion:

A float can receive a double as a parameter:

```c#
int i = 1;
float f = i;
```

But an int can't be cast to a byte automatically:

```c#
int i = 1;
byte b = i; //won't compile
```

Just manually:

```c#
int i = 1;
byte b = (byte)i;
```

For casting a string to a number, for example:

```c#
string s = "1";
int i = Convert.ToInt32(s);
//or
int i = int.Parse(s);
```

### Visual Studio shortcuts:

#### Prop:

Write 'prop' and two-tab it to make a new property fast.