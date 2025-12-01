---
title: "Writing a Compiler: Parsing"
date: 2025-12-01T11:59:22-05:00
draft: true
---

When creating a programming language, the design choice that users will most frequently interact with is the language syntax. The choices you make here will effect every single line of code that is written in your language.

Obviously, the syntax of our language is extremely important. But how can we represent our language, and how can we turn a series of characters into something usable by our Compiler?

```
Start  ::= Expr $

Expr   ::= 'let' id '=' Expr 'in' Expr
         | Expr '+' Factor
         | Factor

Factor ::= Factor '*' Term
         | Term

Term   ::= '(' Expr ')'
         | num
         | id
```

```
Start  ::= Expr $

Expr   ::= 'let' id '=' Expr 'in' Expr
Expr   ::= Expr '+' Factor
Expr   ::= Factor

Factor ::= Factor '*' Term
Factor ::= Term

Term   ::= '(' Expr ')'
Term   ::= num
Term   ::= id
```

Our language:
\[
\Sigma = \{ +, *, =, \text{'let'}, \text{'in'}, \text{num}, \text{id} \}
\]

Our `FIRST` table:
```
FIRST = {
  Start: let, (, num, id
  Expr: let, (, num, id
  Factor: (, num, id
  Term: (, num, id
}
```

Our `FOLLOW` table:
```
FOLLOW = {
  Expr: $, +, in, )
  Factor: *, $, +, in, )
  Term: *, $, +, in, )
}
```
