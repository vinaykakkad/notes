---
id: j9y5pz6ueb0uong1v6f1unc
title: Var Let Const
desc: ''
updated: 1696333457934
created: 1666015367380
---

# Lexical environment and scope

- memory space of the current execution context + LE of parent
- recursive expansion (LE of parent -> LE of parent of parent ) is `scope chain`
  - recursively we reach the global
  - ***parent of global is none****
  - ***LE of some parent function is stored as closure***

## Scope

- part of which can access a variable is scope of variable

# Shortest JS code

- even when we don't have anything in our code, JS engines creates a global object
  - window in case of browsers
  - and in the global context `this` variables refers to the global object

![](/assets/images/2022-10-17-20-30-44.png)

# Let and Const

- memory is assigned before execution to every variable(var, let, const)
- but in case of `let` and `const` memory is not allocated in the global space
  - it is allocated in something, that is known as the `temporal dead zone`
  - ***therefore we cannot access let and const variable without initialization***
  - ***it will give us an reference error***
  - return values for:
    - var without initialization: `undefined`
    - let, const without initialization: `reference error`
    - any variable without declaration: `reference error`

## Re-declaration vs re-initialization

- only var can be re-declared in the same scope
- var and let can be re-initialized, const cannot be
- const cannot be declared without initialization

## Errors

- syntax error: when we re-declare some variable
  - or when we declare const without initialization
- type error: when we re-initialize cost
- reference error: when we access something that is not in the current memory space (TDZ or un-declared)

# Block Scope

- block or compound statement
  - group of statement surrounded within curly braces
- block scoped variables
  - `let` and `const` are block scoped variables
    - i.e. if they are defined within a block, they won't be accessible outside it
      - ***will throw reference error(not defined)***
  
<blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">- let and const are block scoped => their memory allocation will happen in the nearest block memory space<br>- var is function scoped=> its memory allocation will happen in the nearest function memory space</blockquote>

## Shadowing

- shadowing is when a globally declared variable is used / declared inside a block scope
  - for `var`
    - as it is not block scope, the new variable refers to the same memory address
    - **_`var` is function scope_**
  - for `let` and `const`
    - the are block scoped variables
    - memory is allocated in a separate memory space (block)

### Illegal Shadowing

- when a `let` or `const` variable is declared in global scope and we try to declare a `var` variable inside a block
  - it will throw an syntax error due to `illegal-shadowing`

![](/assets/images/2023-10-03-17-13-44.png)