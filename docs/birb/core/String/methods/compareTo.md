---
grand_parent: String
parent: Methods
nav_order: 1
title: compareTo
---

# compareTo method

int compareTo(String str)

Compares the codeUnits of this String to `str`. The returned in is negative if this String is ordered before `str`, positive if after and zero if they are the same. 

## Example
```dart
String birb = "birb";
 int compareValue = birb.compareTo("seeb"); // -1
```
