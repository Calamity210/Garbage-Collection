---
parent: Birb
nav_order: 0
title: Basics
---

# Basics

Birb is interpreted to c++.

## Data Types

Supported data types yet are:

- int - Basic integer type, 64-bit 2's complement.
- double - Birb doubles are 64-bit floating-point numbers as specified in the IEEE 754 standard. 1 bit for the sign, 11 for exponents and 52 for the value itself.
- String - Literals (char array), surrounded by `"`s.
- bool - true or false.
- List - A collection of objects with a length.
- Map - Key / Value pairs, key must be a String.
- class - Encapsulates data fo an object.


## Variables

Variables in Birb are *Explicitly Typed* meaning its type must be declared. Birb is also lexically scoped.

## Comments

Comments are similar to a majority of other languages;
`//` For single-line and `/* */` for multi-line.

```dart
// This is a single-line comment.

/*
This is a multi-line comment.
*/
```