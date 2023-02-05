---
id: 9iyitjbahuhp1l0cy75kxvv
title: Asynchrnous Programming
desc: ''
updated: 1674886881939
created: 1673269366201
---

# Asynchronism

- occurrence of events independent of the main program flow
  - not limited to multiple threads / processes

## Why Async?

![](/assets/images/2023-01-09-18-49-42.png)

- due to the `GIL`, python will have multiple threads at single time, but it still runs a single **CPU instruction** at single time
  - there are ways to go around the `GIL` with `multiprocessing` and `c-python`

<blockquote style="background-color: #0096FF20; padding:4px 3px; border-radius: 5px; border-left: 0.25em solid #0096FF; padding-left: 0.75em">Python runs thread concurrently, but not in parallel</blockquote>

<details>
<summary>concurrent and parallel</summary>

![](/assets/images/2023-01-10-11-38-43.png)

</details>

- in general:
  - multithreading is good for **io-bound** tasks
  - multiprocessing is good for **cpu-bound** tasks

### Generator Analogy for async

- [[capture.dev.python.functional-programming.generators]] does work in chunks of multiple `next()` executions
  - similarity: work is picked-up where we last left the execution in `async` and in `generator`
  - `async` would give the control to some other `coroutine` when it is being waited

# Example

- [code link](https://github.com/mikeckennedy/async-await-jetbrains-webcast/tree/master/code/producer_consumer)

<details>
<summary>Performance Improvements</summary>

![](/assets/images/2023-01-10-13-33-13.png)

![](/assets/images/2023-01-10-13-33-27.png)

</details>

## Async function anatomy

![](/assets/images/2023-01-10-13-32-24.png)

# Common methods of asyncio

- `coroutines`
- `asyncio.run()`
- `asyncio.wait_for()`
- `execute`
- `task` and `create_task`
- loops
  - `get_event_loop`
  - `run_until_complete`
  - `close`

# TODOs

- remaining part from jetbrains videos
- comparison with js (futures and promises)
- ten thousand meters blog
  
- [python docs](https://docs.python.org/3/library/asyncio.html)
  - can start from coroutines and tasks part
