---
title: Introduction to Assembly Part 2
parent: Assembly
---

# Introduction to Assembly Part 2 

In this part we will be covering how to get nasm up and running on your machine for Windows, you can also follow along on x86-64 linux. I personally will be using WSL(Window's Subsystem for linux) with ubuntu 

---

## Installing NASM

This should be extremely simple, pop up your terminal and enter the following commands.
1. `sudo apt-get update -y` -
This command will simply update package repositories and get latest package information.
2. `sudo apt-get install -y nasm` -  This will install the necessary dependencies and packages.

## Special Registers

We are almost to the fun part, this section is more of a reference sheet than something you ***need*** to know. Referenced from [`https://www.cs.uaf.edu/2017/fall/cs301/reference/x86_64.html`](https://www.cs.uaf.edu/2017/fall/cs301/reference/x86_64.html)

| Name | Notes | Type | 64-bit long | 32-bit int | 16-bit short | 8-bit char |
|---|---|---|---|---|---|---|
| rax | Values are returned from functions in this register. | scratch | rax | eax | ax | ah and al |
| rcx | Typical scratch register.  Some instructions also use it as a counter. | scratch | rcx | ecx | cx | ch and cl |
| rdx | Scratch register. | scratch |  |  |  |  |
| rbx | *Preserved register: don't use it without saving it!* | *preserved* | rbx | ebx | bx | bh and bl |
| rsp | *The stack pointer. Points to the top of the stack* | *preserved* | rsp | esp | sp | spl |
| rbp | *Preserved register. Sometimes used to store the old value of the stack pointer, or the "base".* | *preserved* | rbp | ebp | bp | bpl |
| rsi | Scratch register used to pass function argument #2 in 64-bit Linux.  In 64-bit Windows, a preserved register. | scratch | rsi | esi | si | sil |
| rdi | Scratch register and function argument #1 in 64-bit Linux.  In 64-bit Windows, a preserved register. | scratch | rdi | edi | di | dil |
| r8 - r11| Scratch register.  These were added in 64-bit mode, so they have numbers, not names. | scratch | r8 - r11 | r8d - r11d | r8w - r11w | r8b - r11b |
| r12 - r15 | Preserved register.  You can use it, but you need to save and restore it. | scratch | r12 - r15 | r12d - r15d | r12w - r15w | r12b - r15b |

Scratch registers are registers that can be overwritten and used for anything. Preserved Registers have to be put back. You should ***save the register*** if you want to use it.

- A 64 bit linux machine passes function parameters in rdi, rsi, rdx, rcx, r8, and r9.  Any additional parameters get pushed on the stack.  OS X in 64 bit uses the same parameter scheme.

Another thing to keep in mind is the size of datatypes, some common ones are.

| datatype | bits | bytes |
|---|---|---|
| char | 8 | 1 |
| short | 16 | 2 |
| int | 32 | 4 |
| long | 64 | 8 |

## First Program

From here on out it will be mostly programming breaks in between to mention or focus on a point.

The programs may look overwhelming, but I will try my best to go over them and break them down to the best of my ability. Go over them with diligence, and you should be good to go!

Let's keep it simple and start with an `exit code`. All the code will do is exit, but it should be good enough to get started with slightly larger programs. 

First comes a simple plan;
```x86asm
The purpose of the code is to exit and return a status code.

No input will be needed in this program as we are hard-coding everything

Now we need to plan our variables,

First we need to exit the program, for which we will need to call the kernel, 
a.k.a preforming a system call.
A system call requires the system call number to be stored in the rax register,
so rax will be our first variable.

An exit system call requires the status code to be stored in the rbx register so
rbx is our second variable.

rax for the system call number
rdi for the status code
```
 
How do we know what register we need? Refer to [https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/](https://blog.rchapman.org/posts/Linux_System_Call_Table_for_x86_64/).

- Start off by creating a file called exit.asm

Actually before we dive into the code, lets briefly mention sections. A section is the smallest unit of an object file (You can ignore this definition).

For now, we will only use the `.text` section but keep the following sections in mind;

- `.data`
- `.bss`
- `.init`
and maybe even
- `.rodata`

There are others, but these should be enough for now.

We start by defining `_start`, _start can be thought of as the `main` function in multiple other languages (It isn't necessarily the same, but it's a good place to start for now).
We mark _start as `global` so it that is gets added into the object code, if we do not mark it as global  the linker will have no way of knowing about it.

```x86asm
global _start
```

Alright! Now we use our `.text` section, the `.text` section is generally where all your code will lie. Constant data will go into `.data` and we will into the rest when they are needed. So create a `.text`
section.

```x86asm
SECTION .text
```

The next part is where we give our instructions, start by placing the `_start` label.

```x86asm
_start:
```

So we mentioned above the variables needed to make an exit call, lets put those in place. If you refer to the link I mentioned below our variable you will see that the system call code for `sys_exit` is 60 so we know that `rax` will hold 60. It doesn't really say anything for rdi, it just lets you know that is where the status code should go, so we can arbitrarily choose a number. I will be going with 0 solely because it is an often used number to show that there are no errors.

```x86asm
mov     rax, 60 ; We placed the sys_exit code into the rax register
mov     rdi, 0  ; We placed our status code inside the rdi register
syscall         ; We called the kernel
```

That's it! Keep in mind that everything after `;` is a comment. The code in one piece should look like this.

```x86asm
            global _start

            SECTION .text
_start:     mov     rax, 60
            mov     rdi, 0
            syscall         ; A legacy way of calling syscall is int 0x80 or int 80h
``` 

Open your terminal, navigate to the directory with the exit.asm file in it and enter the following commands;

`nasm -f elf64 -o hello.o hello.asm`

This should output a `hello.o` file, now we link it by running:

`ld -o hello hello.o`

This will out put an executable file that you can run by running:

`./hello`

Now if you enter `echo $?` you should see your status code as the output.

```
$: nasm -f elf64 -o hello.o hello.asm
$: ld -o hello hello.o
$: ./hello

0
```

You can mess around with the code to better understand how it works. That's it for now, next time we will go with the traditional hello world program, with a small twist.
