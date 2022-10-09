---
id: r81rounrbl7dbjbbax7zvzk
title: How JS Works
desc: ''
updated: 1665322186026
created: 1665321974645
---

- everything in JS happens inside an `execution context`

# Execution Context

![](/assets/images/2022-10-09-18-59-44.png)

- has two main components
  - `variable environment` or `memory-space` for storing key value pairs of variables and functions
  - `thread of exection` or `code-component` where code is executed

# How Code is executed

- code is executed in two phases
  - *phase 1*: memory allocation
    - key value pairs for all variables and functions are stored
      - variables are stored as undefined
      - for functions the entire code is stored in memory
  - *phase 2*: execution
    - line by line execution and variables are executed
    - after function a new context(in call stack) is created and entire process is repeated
    - after returning the new context is deleted and control is returned back to global context

## Call Stack

- global context always at the bottom
- others are pushed at the time of functions
- contexts are popped when control is returned
