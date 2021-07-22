# C#

"C# is a modern, object-oriented, component-oriented and type-safe programming language, and it provides language constructs to directly support these concepts, making C# a natural language in which to create and use software components. Since its origin, it has added features to support new workloads and emerging software design practices, enabling developers to build many types of secure and robust applications that run in the .NET ecosystem. C# has its roots in the C family of languages and will be immediately familiar to C, C++, Java, and JavaScript programmers", [Microsoft on C#](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/).

## Concepts:

### C# and .NET:

C# is a programming language, whereas .NET is a framework for building applications on Windows. For example, F# can be used with .NET.

.NET basically consists of two components, the Common Language Runtime (CLR) and the Class Library.

### CLR:

First, C# borrows from Java, and translates the code to Intermediate Language Code, more or less what in Java is called ByteCode. Then, compared to Java where the ByteCode is interpreted by the JVM, the IL Code is interpreted by the CLR. The latter process is called Just-in-time Compilation (JIT).

### Classes:

Classes are containers that hold data (attributes) and methods (functions).

### Namespaces:

Namespaces are containers of related classes.

### Assembly:

Assemblies are containers of related namespaces. Physically, a file on the disk, as an DLL (Dynamically Linked Library) or executable file. So, an complete application can consist of one or many assemblies bundled together, depending on how the app's structured.

## Hello World:

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

## Project Layout:

Under a "Solution", there will exist one or many more projects, each with the following layout:

### Properties:

A folder that has the `AssemblyInfo.cs` file. This is the info that will be used to mount the assembly that will be produced as a result of the compilation.

### References:

To add.

### App.config:

To add.

### Program.cs:

To add.