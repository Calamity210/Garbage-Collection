---
parent: Birb
nav_order: 1
title: Control Flows
---

# Control Flows

Control flows in Birb are quite different in what you may see in the majority of languages.

## Loops

While loop
```dart
int i = 0;

while(i < 9) {
  screm(i);
  i++;
}
```

A for loop requires an `initialization, condition, and change`. Separate them with a semicolon `;`.

```python
for (int i = 0; i < 9; i++) {
    screm(i);
}
```

In both cases the braces `{}` are only required if you are specifying more than one statement.

## If / else / ternary

If statements in Birb work just like they would in other languages. Just as loops, the brackets are optional unless you are specifying more than one statement.

```python
int i = 10;

if (i < 10)
screm(i);
else 
screm('i is not less than 10');

foo == 10 ? 
print("Foo is 10") :
print("Foo is not 10");

```

