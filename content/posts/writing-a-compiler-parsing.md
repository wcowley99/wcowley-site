---
title: "Writing a Compiler: Parsing"
date: 2025-11-24T20:52:17-05:00
draft: true
---

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

Our `FOLLOW` table:
```
FOLLOW = {
  Expr: $, +, in, )
  Factor: *, $, +, in, )
  Term: *, $, +, in, )
}
```
