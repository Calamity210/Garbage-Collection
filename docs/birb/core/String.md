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
- [codeUnits](/docs/birb/core/String/properties/codeUnits.md)
- [isEmpty](/docs/birb/core/String/properties/isEmpty.md)
- [isNotEmpty](/docs/birb/core/String/properties/isNotEmpty.md)
- [length](/docs/birb/core/String/properties/length.md)

## Methods
- [codeUnitAt](/docs/birb/core/String/methods/codeUnitAt.md)
- [compareTo](/docs/birb/core/String/methods/compareTo.md)
- [contains](/docs/birb/core/String/methods/contains.md)

# WIP
- [endsWith](/docs/birb/core/String/methods/endsWith.md)
- [indexOf](/docs/birb/core/String/methods/indexOf.md)
- [input](/docs/birb/core/String/methods/input.md)
- [lastIndexOf](/docs/birb/core/String/methods/lastIndexOf.md)
- [padLeft](/docs/birb/core/String/methods/padLeft.md)
- [padRight](/docs/birb/core/String/methods/padRight.md)
- [replaceAll](/docs/birb/core/String/methods/replaceAll.md)
- [replaceFirst](/docs/birb/core/String/methods/replaceFirst.md)
- [replaceRange](/docs/birb/core/String/methods/replaceRange.md)
- [split](/docs/birb/core/String/methods/split.md)
- [startsWith](/docs/birb/core/String/methods/startsWith.md)
- [substring](/docs/birb/core/String/methods/substring.md)
- [toBinary](/docs/birb/core/String/methods/toBinary.md)
- [toDec](/docs/birb/core/String/methods/toDec.md)
- [toHex](/docs/birb/core/String/methods/toHex.md)
- [toOct](/docs/birb/core/String/methods/toOct.md)
- [toLowerCase](/docs/birb/core/String/methods/toLowerCase.md)
- [toUpperCase](/docs/birb/core/String/methods/toUpperCase.md)
- [trim](/docs/birb/core/String/methods/trim.md)
- [trimLeft](/docs/birb/core/String/methods/trimLeft.md)
- [trimRight](/docs/birb/core/String/methods/trimRight.md)
