---
id: ztnm6bj51bu4saqs0m9lg4j
title: Generators
desc: ''
updated: 1673326092823
created: 1673322981537
---
# What is a generator?

1. generator is a function:
   - that returns an object when you call `next()`
     - stores the state between multiple `next()` executions
     - `next()` can be called until we encounter a `StopIteration`
2. generator is a function:
   - that behaves like an `iterator`

# Example(use case)

- we write a program that makes a list of first

## The non-efficient way

```python
def first_n(n):
    '''Build and return a list'''
    num, nums = 0, []
    while num < n:
        nums.append(num)
        num += 1
    return nums
   
   
sum_of_first_n = sum(first_n(1000000))
```

- this will create the entire list in memory
  - **_would be very bad if we something other than integer(ex: file)_**

## Efficient Custom Iterator way

- adding the `__iter__` and `__next__` methods
- sum will now take values using the `next()`

```python
class first_n(object):


    def __init__(self, n):
        self.n = n
        self.num = 0


    def __iter__(self):
        return self


    def __next__(self):
        if self.num < self.n:
            cur, self.num = self.num, self.num+1
            return cur
        raise StopIteration()


sum_of_first_n = sum(first_n(1000000))
```

- this is memory efficient, but there is still a lot of boilerplate code

## Efficient Generator Way

```python
def firstn(n):
    num = 0
    while num < n:
        yield num
        num += 1

sum_of_first_n = sum(firstn(1000000))
```

# Understanding Generator

- generator looks like a normal function, except for the `yield` statement
  - `yield` sends the value back to the caller like return, **_but the function_** is not exited yet
  - the **state** of the function is stored until the next `next()` function call (implicitly using `for` or explicitly using `next()`)
  
## Understanding the `yield` statement

- the `next()` call on a generator object triggers the execution of function until a `yield` statement is encountered
  - on encountering `yield` the value is returned and that **state** is saved
  - this includes
    - any local variables
    - instruction pointer
    - internal stack
    - exception handling
- the next `next()` continues the execution of function right below the `yield statement`
  - if there is no next yield in the function, a `StopIteration` error would be thrown

```python
>>> def multi_yield():
...     yield_str = "This will print the first string"
...     yield yield_str
...     yield_str = "This will print the second string"
...     yield yield_str
...
>>> multi_obj = multi_yield()
>>> print(next(multi_obj))
This will print the first string
>>> print(next(multi_obj))
This will print the second string
>>> print(next(multi_obj))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
```

# Tradeoffs (memory vs speed)

- generators are memory efficient but can be slow
- [generator vs list comprehension -- profiling](https://realpython.com/introduction-to-python-generators/#profiling-generator-performance)

# Further Reading

- [real python article](https://realpython.com/introduction-to-python-generators/#profiling-generator-performance)
- [ ] advanced generator methods
  - [ ] `.send()`
  - [ ] `.throw()`
  - [ ] `.close()`
- [ ] use (data pipeline)
