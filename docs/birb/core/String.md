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
- [codeUnits](/docs/birb/core/String/properties/codeUnits.html)
- [isEmpty](/docs/birb/core/String/properties/isEmpty.html)
- [isNotEmpty](/docs/birb/core/String/properties/isNotEmpty.html)
- [length](/docs/birb/core/String/properties/length.html)

## Methods
- [codeUnitAt](/docs/birb/core/String/methods/codeUnitAt.html)
- [compareTo](/docs/birb/core/String/methods/compareTo.html)
- [contains](/docs/birb/core/String/methods/contains.html)

# WIP
- [endsWith](/docs/birb/core/String/methods/endsWith.html)
- [indexOf](/docs/birb/core/String/methods/indexOf.html)
- [input](/docs/birb/core/String/methods/input.html)
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
