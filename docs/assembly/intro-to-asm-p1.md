---
title: Introduction to Assembly Part 1
parent: Assembly
---

# Introduction to Assembly

In this series we will be(hopefully) going through all necessary fundamentals to learn assembly. Most of the work will be with 64-bit nasm, but occasionally I may include x86\. Feel free to contact me at <mark>aayanraja210@gmail.com</mark> or you can join the SPI Discord at [https://discord.gg/24aS9Dk](https://discord.gg/24aS9Dk)

---

## Assembly

Before we dive into learning, let's try understanding what assembly really is. Assembly for the most part is the most basic language for any processor. You, as the programmer, will only work with operations implemented directly on the CPU. Unlike the languages most of you are probably used to, assembly lacks conveniences such as variables and functions. I mentioned above that I will mostly be using x86-64, but why does that matter? It matters because assembly is not portable between families of processors. Learning assembly will definitely help you gain(or improve) the ability to write effective code in high-level languages

## The Basics

Yup, back to square one...the good ol' basics. But basics when learning asm(I will be using the term asm a lot, it is an abbreviation for assembly) are not data types, loops, functions, classes, comments, OOP and whatnot, but rather what a computer is and how it works. To be more specific, the CPU and memory. If you can grasp this, the rest of the journey will definitely be a whole lot easier. We all know that a computer program is nothing but a collection of numbers stored in memory. Different numbers means different results. The CPU reads one number at a time, decodes them and then executes them. This is known as the <mark style="background-color: violet;">fetch-execute cycle</mark>. There are a couple of elements required for the fetch-execute cycle:

*   Program Counter

-- Figures out where to fetch the next instruction.

*   Instruction Decoder

-- The name pretty-much says it all, it figures out what the instruction means.

*   Data Bus

-- Fetches the memory location for the calculation

*   <mark style="background-color: #34ebde;">Registers</mark>

-- These are extremely important, make sure you understand them. A register can hold an instruction, storage address, or any kind of data (such as a bit sequence or individual characters). Some instructions specify registers as part of the instruction. For example, an instruction may specify that the contents of two defined registers be added together and then placed in a specified register. To expand on that example, when you instruct to add. The specified registers will automatically be checked for the required information. Also keep in mind that a register must be large enough to hold an instruction, ex: 64 bit in length on a 64-bit computer. All things like, addition, multiplication, comparisons, etc... generally use registers. General purpose registers to be exact. But you have to keep in mind that registers are limited and there are only a few. Information is generally stored in main memory, brought to registers for processing and then put back into the memory. We will get into more details in a bit.

Data and decoded instructions are passed onto the the arithmetic and logic units for further processing, the instructions are then carried out. Once the results of the computation are calculated, they are placed on the data bus and sent to the appropriate location in memory or within a register as specified by the instructions.

## Computer Memory

As I mentioned earlier, computer memory is a sequence of fixed size storage locations called an <mark style="background-color: #eb8634;">address</mark>. The size of a single storage location is called a <mark>byte</mark>.

## Registers

Yes, we're back to registers! There's not much more to say about them. Just remember, registers are usually used for computation. Think of a register like a desk, it holds the things that you are currently working with on it, while the rest is put away. Registers on computers nowadays are 4 bytes long a.k.a 1 <mark style="background-color:#34e343">word</mark> long. The size of a typical register is called a word

## Addresses

Addresses are also 1 word long and therefore fit inside a register. Addresses stored in memory are called <mark style="background-color: #28bf79;">pointers</mark> because they _"point"_ you to a different location in the memory.

## Data Accessing Methods

There's been a lot of information to cover, but we are finally getting closer to asm. Data accessing modes or methods are different ways a processor can adopt to access data. The general form of memory address references is this:

**ADDRESS_OR_OFFSET(%BASE_OR_OFFSET,%INDEX,MULTIPLIER)**

or,

**BaseAddress( %Offset, %Index, DataSize)**

These are the same as doing:

**FINAL ADDRESS = ADDRESS_OR_OFFSET + %BASE_OR_OFFSET + MULTIPLIER * %INDEX**

or,

**Final_address = BaseAddress + %Offset + (DataSize x %Index)**

I won't spend time explaining those, read through them carefully and they should be fairly simple. There are the following ways to access data:

**1\.** Immediate Addressing Mode: the data is embedded in the instruction itself. For example, if we want to initialize a register to let's say 20, instead of giving the computer an address to read the 20 from, we would initiate immediate mode, and directly give it the number 20.

**2\.** Direct Addressing Mode: The instructions contain the memory address to access. This is done by solely by using ADDRESS_OR_OFFSET or BaseAddress, and rests of the fields have been substituted with zero in the equations above.

**3.** Indirect Addressing Mode: In the indirect addressing mode, the instruction contains a register that contains a pointer to where the data should be accessed. Indirect addressing mode loads a value from the address indicated by a register.

**4.** Indexed Addressing Mode: In the indexed addressing mode, the instruction contains a memory address to access, and also specifies an index register to offset that address.You can use any general-purpose register as the index register. You can also have a constant <mark>multiplier of 1, 2, or 4</mark> for the index register, to make it easier to index by bytes, double-bytes, and words.

**5\.** Base Pointer Addressing Mode : Base pointer addressing is similar to indirect addressing, except that it adds a constant value to the address in the register.

**6\.** Register addressing mode: In the register addressing mode, the instruction contains a register to access, rather than a memory location. The rest of the modes will deal with addresses. Register mode simply moves data in or out of a register.

## Wrap Up

There was a lot of information to cover, but all of this is essential to learning to program using asm. We will take a look at some programs in a variety of languages and compare them with asm, and then we will gradually move towards nasm. Don't worry if you can't grasp everything here, we will refer back to it through out the series so you will get a better understanding soon enough.

Please suggest anything you would like me to change and let me know how I can improve... is there something you think I should touch upon? Thanks, and I'll see you in the next one!

## Take Care!
