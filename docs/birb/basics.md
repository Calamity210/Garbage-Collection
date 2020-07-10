---
parent: Birb
nav_order: 1
title: Basics
wip: true
---

# Basics

## Data Types

The only supported data types yet are:

- Int - basic integer type, guaranteed to have a width of at least 16 bits.
- Double - Birb doubles are 64-bit floating-point numbers as specified in the IEEE 754 standard. 1 bit for the sign, 11 for exponents and 52 for the value itself.
- String - Literals (char array), surrounded by `"`s.
- Bool - True/False.
- Tuples - An (currently) immutable object that holds multiple elements. Created by combining multiple expressions with a comma; `tuple => 1, 2.5, 21` . By default, tuple elements are named alphabetically, `a, b, c, d ...`. 

## Operators

Although the majority of operators in Birb work just as they would the majority of other languages, the assignment operator is `=>` rather than `=`.
The same is used to denote parameters being passed to a function.

ie: `tweet => "Henlo Birb"` would print `Henlo Birb`.

## Variables

Variables in Birb are *Implicitly Typed* meaning its type will be deduced without having the need to be specified.
Constant values (values known at compile time) are denoted by `::`.

```javascript
var :: "Henlo Birb" // Constant
var1 => "Henlo Birb" // String
var2 => 14 // Int
var 3 => 14.0 // Double, you can also do 14d
```

Variable names, as well as all other identifiers cannot begin with a number

To explicitly convert a variable's type follow the `name => type => value` format.

`ie: double => Double => 21`
## Comments

Comments are similar to a majority of other languages;

`//` For single-line and `/* */` for multi-line.

```dart
// This is a single-line comment.

/*
This is a multi-line comment.
*/
```