# Objected-Oriented Programming

The goal for OOP is having a good abstraction level, encapsulation, inheritance
and polymorphism. It aims to be as close as possible to the what we would put as
being the business rules, with classes and objects representing real-world
concepts.

# Contents:

- [Objected-Oriented Programming](#objected-oriented-programming)
- [Contents:](#contents)
  - [1. Concepts:](#1-concepts)
    - [1.1. Abstraction:](#11-abstraction)
    - [1.2. Encapsulation:](#12-encapsulation)
      - [1.2.1 Modifiers:](#121-modifiers)
    - [1.3. Inheritance:](#13-inheritance)
    - [1.4. Polymorphism:](#14-polymorphism)
      - [1.4.1. Overload or Early Binding:](#141-overload-or-early-binding)
      - [1.4.2. Override or Late Binding:](#142-override-or-late-binding)
      - [1.4.3 Abstract Classes:](#143-abstract-classes)
      - [1.4.4 Interfaces:](#144-interfaces)
  - [2. Javascript OO:](#2-javascript-oo)
    - [2.1: Typescript OO:](#21-typescript-oo)

## 1. Concepts:

### 1.1. Abstraction:

"Abstraction is one of the key concepts of object-oriented programming (OOP)
languages. Its main goal is to handle complexity by hiding unnecessary details
from the user. That enables the user to implement more complex logic on top of
the provided abstraction without understanding or even thinking about all the
hidden complexity", [Stackify](https://stackify.com/oop-concept-abstraction/).

### 1.2. Encapsulation:

"By definition, encapsulation describes the idea of bundling data and methods
that work on that data within one unit, like a class in Java. This concept is
also often used to hide the internal representation, or state of an object from
the outside. This is called information hiding", [Stackify](https://stackify.com/oop-concept-for-beginners-what-is-encapsulation/).

#### 1.2.1 Modifiers:

In most OO languages there are modifiers that change access to properties and 
methods. They are:

- Private: Only the class has access to the properties and methods;
- Default: Automatically assigned when no properties are defined, only gives
access to the properties and methods to classes in the same package;
- Protected: The same as default, but also gives access to classes that
extend them;
- Public: All classes have access to the properties and methods.


### 1.3. Inheritance:

"Inheritance is one of the core concepts of object-oriented programming (OOP)
languages. It is a mechanism where you can to derive a class from another class
for a hierarchy of classes that share a set of attributes and methods. You can
use it to declare different kinds of exceptions, add custom logic to existing
frameworks, and even map your domain model to a database", [Stackify](https://stackify.com/oop-concept-inheritance/).

### 1.4. Polymorphism:

"Polymorphism is one of the core concepts of object-oriented programming (OOP)
and describes situations in which something occurs in several different forms.
In computer science, it describes the concept that you can access objects of
different types through the same interface. Each type can provide its own
independent implementation of this interface", [Stackify](https://stackify.com/oop-concept-inheritance/).

#### 1.4.1. Overload or Early Binding:

"Overloading a method simply means two or more methods have the same method name
with different arguments or parameters(compulsory) and return type 
(not necessary)", [Medium](https://medium.com/@atandaoluchiaminat/overload-vs-override-in-object-oriented-programming-oop-a38ca0ccaf40).

#### 1.4.2. Override or Late Binding:

"Overriding a method simply means that a subclass redefines its inherited
method(s) when it needs to change or extend the behavior of that method",
[Medium](https://medium.com/@atandaoluchiaminat/overload-vs-override-in-object-oriented-programming-oop-a38ca0ccaf40).

#### 1.4.3 Abstract Classes:

Abstract classes are templates of a class, that can't be instantiated. They can
represent a general concept, that serves as a model for other classes to
inherit. For example:

```java
abstract class Shape{  
  abstract void draw();  
}  
/*In a real scenario, implementation is provided by others i.e.
unknown by end user*/  
class Rectangle extends Shape{  
  void draw(){System.out.println("drawing rectangle");}  
} 

class Circle1 extends Shape{  
  void draw(){System.out.println("drawing circle");}  
}  

//In a real scenario, the method is called by the programmer or user  
class TestAbstraction1{  
  public static void main(String args[]){  
    Shape s = new Circle1();
    /*In a real scenario, object is provided through method, e.g.,
    getShape() method*/  
    s.draw();  
  }  
}  
//Source: https://www.javatpoint.com/abstract-class-in-java (adapted)
```

#### 1.4.4 Interfaces:

"To sum it up:
When you write an interface, you're basically saying: 'I need something that
..'", [Yehuda Shapira](https://stackoverflow.com/questions/2866987/what-is-the-definition-of-interface-in-object-oriented-programming).

We can define just attributes/method signatures, or we can have a default
implementation.


## 2. Javascript OO:

Some different syntaxes are used in JS for specific OO implementation. Example:

```js
class Polygon{
  constructor(height, width){
    this.height = height;
    this.width = width;
  }

  //the # specifies private 

  get area(){
    return this.#calculateArea();
  }

  #calculateArea(){
    return this.height * this.width;
  }
}

class Triangle extends Polygon{
  /*to add statements to the previous constructor we would need to use this
  code, but since we aren't going to modify it, we're able to omit it:

  constructor(heigth, width){
    super(heigth, width);
    //(here we define the same parameters to access the same constructor)
    //and starting from here we'd define the additions
  }
  */

  #calculateArea(){
    return (this.height * this.width)/2;
  }
}
```

Also, in JS we can only define one constructor.

### 2.1: Typescript OO:

In TS we can use polymorphism as expected (such as in Java), and define the base
class for manipulation in method signatures. Example:

```ts
class Animal {
  name: string;
  constructor(theName: string) {
    this.name = theName;
  }
  move(distanceInMeters: number = 0) {
    console.log(`${this.name} moved ${distanceInMeters}m.`);
  }
}

class Snake extends Animal {
  constructor(name: string) {
    super(name);
  }
  move(distanceInMeters = 5) {
    console.log("Slithering...");
    super.move(distanceInMeters);
  }
}

class Horse extends Animal {
  constructor(name: string) {
    super(name);
  }
  move(distanceInMeters = 45) {
    console.log("Galloping...");
    super.move(distanceInMeters);
  }
}

let sam = new Snake("Sammy the Python");
let tom: Animal = new Horse("Tommy the Palomino");


function test(animal:Animal){
  console.log(animal.name);
}

test(sam); //"Sammy the Python"
test(tom); //"Tommy the Palomino"
```