# Data Structures

"A data structure is a storage that is used to store and organize data. It is a
way of arranging data on a computer so that it can be accessed and updated
efficiently. A data structure is not only used for organizing the data. It is
also used for processing, retrieving, and storing data. There are different
basic and advanced types of data structures that are used in almost every
program or software system that has been developed. So we must have good
knowledge about data structures", [G4G](https://www.geeksforgeeks.org/data-structures/).

# Contents:
- [Data Structures](#data-structures)
- [Contents:](#contents)
- [Structures:](#structures)
  - [Graph:](#graph)
  - [Hash Table:](#hash-table)
  - [Linked Lists:](#linked-lists)
  - [Queue:](#queue)
  - [Stack:](#stack)
  - [Tree:](#tree)
  - [Array:](#array)
  - [Matrix:](#matrix)

# Structures:

## Graph:

Data scructure on which it's possible to define the relationship between elements,
for example, an item (A) can relate only to another item (B), and the latter (B)
is able to relate to 10 (or less/more) previously defined elements.

The relationships are called edges (links/lines), and the elements are often
called vertices, nodes or points.

## Hash Table:

Data structure also known as Hash Map, basically a generalization on the array
structure, but with a hash function that attributes an index to the element
inserted, and the detail that makes this structure faster on some operations
(such as read and search), that is: not ordering data.

## Linked Lists:

That type of list consists of nodes, in which each one contains the data,
and an indication of the next value.

- Simple:
The nodes contain only the next item reference.

- Doubly:
The nodes contain both the previous and next item references.

- Circular:
The first node contains the last item as the previous item reference, and the
last one has the first node as the next.

## Queue:

Data structure on which only one element can be manipulated at a time.

Has both queue and dequeue methods (insert and delete), that realizes the
operation based on the following implementation:

- FIFO:
First In, First Out.

You could say that it's on an inverted order (from the bottom to the top items).

The deleted element using pop method, for that reason, is the first one inserted.

## Stack:

Data structure on which only one element can be manipulated at a time.

Has both push and pop methods (insert and delete), that realizes the operation
based on the following implementation:

- LIFO: 
Last In, First Out.

You could say that it's on a regular order (from the top to the bottom items).

The deleted element using pop method, for that reason, is the last one inserted.

## Tree:

Hierarchy based data structure, on which one element serves as a root, and the
remaining ones are added as leaves (that can be turned into sub-trees, when there
are children), thus the tree nomenclature.

- The "leaf" only points to its children, and not an element points to the root.

## Array:

One of the most basic structures, based on the element's index.

## Matrix:

Arrays inside of arrays.