---
parent: Birb
nav_order: 2
title: Control Flows
---

# Control Flows

Control flows in Birb are quite different in what you may see in the majority of languages.

## Loops

To loop a function as long a condition is met (while loop), place a condition followed by the `do` keyword.
```python
iteration => 0

true do (
    tweet => iteration
    iteration => iteration + 1
)

/*
 This is the equivalent to the following in C:
*/

int iteration = 0;

while(true) {
    printf("%d", iteration);
    iteration++;
}
```

A for loop requires the `initialization, condition, and change` to be placed before the `do` keyword. Separate them with a colon `:`.

```python
i => 1 : i <= 10 : i++ do (
    tweet => i
)

/*
 This is the equivalent to the following in C:
*/

for (int i = 1; i <= 10; i++) {
    printf("%d", i);
}
```

In both cases the brackets `()` are only require if you are specifying more than one statement.

## If / else

If statements in Birb work just like ternary operators in other languages; `?` for if and `:` for else. Place multiple ifs consecutively for an `else if` statement. Just as loops, the brackets are optional unless you are specifying more than one statement.

```python
foo => 10

foo > 10 ? // if (foo > 10)
tweet => foo

foo == 5 ? else if (foo == 5)
tweet => "Foo is 5"

: // else
tweet => "Less than ten and not 5"
```

