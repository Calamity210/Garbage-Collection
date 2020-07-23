---
parent: Birb
nav_order: 0
title: Basics
---

# Basics


## Small program
```dart
class Birb {
  String favouriteGreeting = 'Henlo';
  String name = 'Birb';
  int age = 10;
  List favouriteFood = ['Seeb', 'Seeb', 'Seeb'];
  Map goodBadMap = {
        'good': ['Seeb'],
        'bad': 'rest',
        'goodCount': 1,
        'badCount': 'ERROR'
  };
}


List favouriteFood = Birb.favouriteFood;
Map goodBadMap = Birb.goodBadMap;

void printDetails() {
    screm(Birb.favouriteGreeting + " am " + Birb.name);
    screm("I am " + Birb.age + " years old");
    screm("I like " + favouriteFood[0]);
    screm('There is only ' + goodBadMap['goodCount'] + " item in my good list");
}

printDetails();

```


## Data Types

Supported data types yet are:

- int - Basic integer type, 64-bit 2's complement.
- double - Birb doubles are 64-bit floating-point numbers as specified in the IEEE 754 standard. 1 bit for the sign, 11 for exponents and 52 for the value itself.
- String - Literals (char array), surrounded by either `"` or `'`s.
- bool - true or false.
- List - A collection of dynamic objects with a length.
- Map - Key / Value pairs, key must be a String.
- class - Encapsulates data for an object.

## Primitive Types example
 ```dart
String str = "Henlo birb";

int length = str.length;

double d = length * 0.5;

bool isGreaterThanFive = d > 5;
```

## Class example
```dart
class Birb {

  String name = "Birb";
  int age = 5;
  bool isMale = true;

}
```

## List example
```dart
List list = ["Seeb",10, false];

list.add("More seeb");
list.remove(2);

int length = list.length;
```

## Map example
```dart
Map food = {
  "veg": ["carrot", "lettuce"]
};

List i = food["veg"];

screm(i[0]);
```

## Variables

Variables in Birb are *Explicitly Typed* meaning its type must be declared. 
To define a variable, specify the type, followed by its name and value.

```dart
String foo = "henlo";
```
Birb is also lexically scoped, descendant scopes will access the most recent declared variable

## Comments

Comments are similar to a majority of other languages;
`//` For single-line and `/* */` for multi-line.

```dart
// This is a single-line comment.

/*
This is a multi-line comment.
*/
```