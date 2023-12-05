- python async IO is not threading, nor is it multiprocessing
- async IO is a single-threaded, single-process design: it uses `cooperative multitasking`

<details>
<summary>Simultaneous chess playing Example</summary>

- Chess master Judit Polgár hosts a chess exhibition in which she plays multiple amateur players. She has two ways of conducting the exhibition: synchronously and asynchronously.
- Assumptions:
  - 24 opponents
  - Judit makes each chess move in 5 seconds
  - Opponents each take 55 seconds to make a move
  - Games average 30 pair-moves (60 moves total)
- **Synchronous version**: Judit plays one game at a time, never two at the same time, until the game is complete. Each game takes **(55 + 5) * 30 == 1800** seconds, or 30 minutes. The entire exhibition takes **24 * 30 == 720** minutes, or **12 hours**.
- **Asynchronous version**: Judit moves from table to table, making one move at each table. She leaves the table and lets the opponent make their next move during the wait time. One move on all 24 games takes Judit **24 * 5 == 120** seconds, or 2 minutes. The entire exhibition is now cut down to **120 * 30 == 3600** seconds, or just **1 hour**. [(Source)](https://youtu.be/iG6fr81xHKA?t=4m29s)

</details>

## Rules of asyncio

- syntax `async def` introduces either a **native coroutine** or an **asynchronous generator**
  - expressions `async with` and `async for` are also valid
- keyword `await` passes function control back to the event loop.

```python
async def g():
    # Pause here and come back to g() when f() is ready
    r = await f()
    return r
```

<details>
<summary>explanation</summary>

- If Python encounters an `await f()` expression in the scope of `g()`, this is how `await` tells the event loop, “Suspend execution of `g()` until whatever I’m waiting on—the result of `f()` —is returned. In the meantime, go let something else run.”

</details>

- function that you introduce with `async def` is a **coroutine**
  - To call a coroutine function, you must `await` it to get its results
  - It is less common (and only recently legal in Python) to use `yield` in an `async def` block.
    - This creates an [asynchronous generator](https://www.python.org/dev/peps/pep-0525/), which you iterate over with `async for`.
  - Anything defined with `async def` may not use `yield from`, which will raise a `SyntaxError`.
- it is a `SyntaxError` to use `await` outside of an `async def` coroutine.

<details>
<summary>code examples</summary>

```python
async def f(x):
    y = await z(x)  # OK - `await` and `return` allowed in coroutines
    return y

async def g(x):
    yield x  # OK - this is an async generator

async def m(x):
    yield from gen(x)  # No - SyntaxError

def m(x):
    y = await z(x)  # Still no - SyntaxError (no `async def` here)
    return y
```

</details>

- when you use `await f()`, it’s required that `f()` be an object that is [awaitable](https://docs.python.org/3/reference/datamodel.html#awaitable-objects)
- an awaitable object is either
  1. another coroutine or
  2. an object defining an `.__await__()` dunder method that returns an iterator

## Design Patterns

