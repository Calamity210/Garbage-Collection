---
title: Introduction to Assembly Part 3
parent: Assembly
---

# Introduction to Assembly Part 3

In this part we will be writing a small "Henlo Birb" program and breaking it down into small sections. Why Henlo Birb? Because birbs are cute.

---

## Henlo Birb
 
 Start by creating a new file called `henlo.asm`
 
 Since we already know what our message will be, we'll create a variable for it in the `.data` section.
 
 Create a `.data` section and add a variable called `message` in it. We will also create a len variable in which we will store the length of our string.
 
 When creating a variable we need to tell the program how much memory to initialize, in this case we will use the `db` keyword to initialize memory with one or more bytes.
 You will realize that I add `0Ah` after the variable, this is equivalent to 10 in decimal and stands for the linefeed `\n` (new line).
```asm
SECTION    .data
    message    db  "Henlo Birb!", 0Ah
    len        equ $-message               ; Length of String
```
Fun fact: when we pass "Henlo Birb!" it becomes:
```
"Henl","o Bi", "rb!"
and actually looks like
"Henlo Birb!", 0
```
Now create a `.text` section and _start method.

```asm
    SECTION     .text
    global     _start

_start:
     
```

If you refer to [https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/](https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/) and search for sys_write, you will see that:
 ```
We need a system code of 1
Our file descriptor goes in rdi, 1 is the file descriptor for stdout
Our string itself goes int rsi
and the length of our string goes in rdx
```

```asm
mov     rax, 1          ; sys_write
mov     rdi, 1          ; stdout
mov     rsi, message    ; Henlo Birb (Our message)
mov     rdx, len        ; Length of the message
syscall                 ; Call the kernel
```

If you build and run this program now, "Henlo Birb!" should be printed, but you will encounter a `Segmentation Fault`. This is because the program finished all instructions and does know what to do next, so it chokes. To correct this, we need to exit the program.

```asm
mov     rax, 60     ; sys_exit
mov     rdi, 0      ; Status code
syscall
```

Refer to part two to better understand the above.

Your code should now look like this: 

```asm
SECTION    .data
    message    db  "Henlo Birb!", 0Ah
    len        equ $-message

SECTION     .text
 global     _start

_start:
     mov     rax, 1
     mov     rdi, 1
     mov     rsi, message
     mov     rdx, len
     syscall

     mov     rax, 60
     mov     rdi, 0
     syscall
```

If you run this now, you should have a happy looking `Henlo Birb!` on your screen!

Next time, we will look at functions and create a function to get the length of a string, for now though. I'm out!

![Caique March](https://media.giphy.com/media/XceM7JdQNsl7d4wYtT/source.gif)


[![SpiDev Discord](https://discordapp.com/api/guilds/438111991564075010/widget.png?style=banner4)](https://discord.gg/24aS9Dk)