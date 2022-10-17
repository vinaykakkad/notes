---
id: 71vmk221iuw1r44eg87i9k1
title: Hoisting
desc: ''
updated: 1666015344199
created: 1666015185595
---
# Hoisting in JS

- accessing variables and functions before initialization

## Why this happens

- before the actual execution
  - memory is allocated to every variable and function
  - thus we can access variables before initialization

## Cases

- accessing variable: return `undefined`
- accessing a named function: returns `the code of the function`
- accessing anonymous function: returns `undefined` (is ultimately an variable)
- accessing undeclared variable: returns `not-defined` error
