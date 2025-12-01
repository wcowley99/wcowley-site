---
title: "Writing a Compiler: Introduction"
date: 2025-11-24T12:00:00-05:00
draft: true
---

Welcome to my own home-built course on Programming Languages and Compilers! I always wanted to take Northeastern's course on compilers, but due to some drama in the CS department, the professor that taught Compilers left. So, I decided to create my own "course" as I have researched this topic. Without further ado!

### 1. Definitions

What is a *Programming Language*? What is a *Compiler*? The [Wikipedia definition](https://en.wikipedia.org/wiki/Language) of a language is:

> **Language** is a structured system of communication that consists of grammar and vocabulary.

So a *Programming Language* is some system of communication that allows a human to instruct a computer to do something. A *Compiler* is the implementation of a *Programming Language*.

### 2. An Overview of a Compiler

#### 2.1. The Purpose

![C code compiled to Assembly compiled to Binary](/c-asm-bin.png)

Computers operate in ones and zeros, they have no concept of letters, decimal numbers, or anything else. As a result, programmers created Assemblers that allowed them to write the computer instructions in a human-readable format, and the Assembler would do the work of translating that to machine code. Eventually, languages were created that allowed programmers to express high-level ideas without needing to know exactly what instructions the computer would have to run.

#### 2.2. The Steps of a Compiler

Somehow, we need to take a sequence of arbitrary characters, and, if possible, convert them into a program in binary format that can be executed by the computer.

![The six steps for our Compiler](/compiler-steps.jpg)

Let's define our steps:

1. *Lexing*: We first convert the characters into a list of **lexemes**. A lexeme is a sequence of characters that are assigned some meaning.
2. *Parsing*: We then convert our sequence of lexemes into an **Abstract Syntax Tree** (henceforth **AST**). We'll discus ASTs in depth more later, but for now, know that an AST is a representation of our source code that preserves its meaning, but not its structure.
3. *Optimization*: Now that we have an AST, we can perform analysis on it to optimize it and do any other cleanup that is needed.
4. *Code Generation*: At this step, we convert our AST into assembly code.
5. *Assembling*: Here, we convert our generated assembly code into binary machine code.
6. *Linking*: Finally, we link our code to any necessary dependencies and convert it into an executable format.

The first two steps are often overlooked in other courses on Programming Languages/Compilers because they are often considered the "less interesting" aspect of compiler design. A big reason for this is because lexer and parser design is largely a solved area. However, since the goal of this course is to fully understand how compilers work by implementing our own, and because they are by no means easy, I think it is worthwhile to cover how these steps in the compiler work.

The final two steps will be very simple, as we will use existing Operating System toolchains to do this.

Ultimately, the majority of this course will cover the middle two steps, as there are many language features that we can implement which have profound effects on the design and structure of our Compiler.

### 3. Materials

Below is a list of necessary software and useful reference materials.

#### 3.1. Software

- [Rust](https://rust-lang.org/) - An open-source, rich type system programming language
- [nasm](https://www.nasm.us/) - An open-source assembler
