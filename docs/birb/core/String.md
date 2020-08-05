---
grand_parent: Birb
parent: Core
nav_order: 0
title: String
has_children: true
wip: true
---

# String type

An array of chars (UTF-16) code units.

A data type used mainly to represent text, denoted by the `'` or `"`s its wrapped within.

Strings in birb are multiline by default:

```dart
screm("This string will print on one line");

// OR

screm("
This String
will print on two lines
");
```

You can use the `+` operator to concat Strings:

```dart
screm("Henlo " + "birb!") // "Henlo birb!"
```

## Properties
- [codeUnits](#codeUnits)
- [isEmpty](#isEmpty)
- [isNotEmpty](#isNotEmpty)
- [length](#length)

## Methods
- [codeUnitAt](#codeUnitAt)
- [compareTo](#compareTo)
- [contains](#contains)
- [endsWith](#endsWith)
- [indexOf](#indexOf)
- [input](#input)

# WIP
- [lastIndexOf](/docs/birb/core/String/methods/lastIndexOf.html)
- [padLeft](/docs/birb/core/String/methods/padLeft.html)
- [padRight](/docs/birb/core/String/methods/padRight.html)
- [replaceAll](/docs/birb/core/String/methods/replaceAll.html)
- [replaceFirst](/docs/birb/core/String/methods/replaceFirst.html)
- [replaceRange](/docs/birb/core/String/methods/replaceRange.html)
- [split](/docs/birb/core/String/methods/split.html)
- [startsWith](/docs/birb/core/String/methods/startsWith.html)
- [substring](/docs/birb/core/String/methods/substring.html)
- [toBinary](/docs/birb/core/String/methods/toBinary.html)
- [toDec](/docs/birb/core/String/methods/toDec.html)
- [toHex](/docs/birb/core/String/methods/toHex.html)
- [toOct](/docs/birb/core/String/methods/toOct.html)
- [toLowerCase](/docs/birb/core/String/methods/toLowerCase.html)
- [toUpperCase](/docs/birb/core/String/methods/toUpperCase.html)
- [trim](/docs/birb/core/String/methods/trim.html)
- [trimLeft](/docs/birb/core/String/methods/trimLeft.html)
- [trimRight](/docs/birb/core/String/methods/trimRight.html)

# Properties

## codeUnits

List codeUnits

Returns a list containing the 16-bit Unicode code units of this String.

### Example
```dart
String birb = "birb";
List codeUnits = birb.codeUnits; // [98, 105, 114, 98]
```


## isEmpty

bool isEmpty

True if this String is empty

### Example
```dart
String birb = "birb";
bool isEmpty = birb.isEmpty; // false
```

## isNotEmpty

bool isNotEmpty

True if this String is not empty

### Example
```dart
String birb = "birb";
bool isNotEmpty = birb.isNotEmpty; // true
```

## length

int length

Returns an int containing the length of this String

### Example
```dart
String birb = "birb";
int length = birb.length; // 4
```

# Methods

## codeUnitAt

int codeUnitAt(int index)

Returns the codeUnit at the given index

### Example
```dart
String birb = "birb";
int codeUnit = birb.codeUnitAt(0); // 98
```

## compareTo

int compareTo(String str)

Compares the codeUnits of this String to `str`. The returned in is negative if this String is ordered before `str`, positive if after and zero if they are the same. 

### Example
```dart
String birb = "birb";
 int compareValue = birb.compareTo("seeb"); // -1
```

## contains

bool contains(String other, int startIndex)

Returns true if this String contains `other` at or after the startIndex

### Example
```dart
String birb = "birb";
 int compareValue = birb.contains("seeb"); // false
```

## endsWith

bool endsWith(String str)

Returns true if this String ends with `str` 

### Example
```dart
String birb = "birb";
int compareValue = birb.endsWith("seeb"); // false
```

# indexOf

int indexOf(String str, int start)

Returns the index of the first match of `str` starting from `start` within this `String`

## Example
```dart
String birb = "birb";
 int compareValue = birb.indexOf("b", 0); // 0
```

# input 

int input(String str)

Prints this String before reading a line from StdIn

## Example
```dart
String birb = "birb";
 int compareValue = birb.input("b");
```
