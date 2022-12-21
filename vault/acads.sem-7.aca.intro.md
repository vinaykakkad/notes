---
id: 60ial221sf2kqr5a6v67fjv
title: Intro
desc: ''
updated: 1671597930092
created: 1671597696289
---

- [Lecture 0](#lecture-0)
  - [moore fsm](#moore-fsm)
  - [sequence detector](#sequence-detector)
- [Lecture 2](#lecture-2)
  - [arbiter](#arbiter)
    - [steps](#steps)
  - [hamming Code (1bit error correcting code)](#hamming-code-1bit-error-correcting-code)
  - [CRC (cyclic redundancy check)](#crc-cyclic-redundancy-check)
- [Lecture 3](#lecture-3)
  - [Types of CRC implementation](#types-of-crc-implementation)
    - [Combinational](#combinational)
    - [Iterative](#iterative)
      - [Rolled Version](#rolled-version)
      - [Unrolled Version](#unrolled-version)
    - [Setup Time in Flip-Flops (for iterative versions)](#setup-time-in-flip-flops-for-iterative-versions)
- [Lecture 4](#lecture-4)
  - [LFSR (linear feedback shift register)](#lfsr-linear-feedback-shift-register)
    - [Standard Format](#standard-format)
    - [Modular Format](#modular-format)
      - [Differences](#differences)
    - [LFSR based CRC](#lfsr-based-crc)

# Lecture 0

## moore fsm

![](/assets/images/2022-11-21-11-01-34.png)

- it is a sequential circuit
- combinational circuit followed by flip-flops
- *next state is a function of present state*

## sequence detector

![](/assets/images/2022-11-21-11-15-18.png)

- use cases: *sender and receiver (CN)*, to check for some code(error code)
- steps:
  - start with reset($S_0$)
  - keep expanding leaves
  - discard leaves whose pattern is not required and connect back
- [ ] ***practice some random sequence detector***

# Lecture 2

## arbiter

- allocate access to shared resources
- consider a shared memory and 3 processes
  - input: [r1, r2, r3]
  - output: [a1, a2, a3]
  - arbiter gives ack to one of the process at a time
- types: **priority** based, **history** based

### steps

- write list of states describing the current state of the system
  - used, waiting, not waiting
- [ ] [Arbiter Practice](https://drive.google.com/drive/u/1/folders/14yvGxRrt4DxzK01nqcRt2KcST_RHMpMS)
- [ ] ***write states for priority and history based***
- [ ] ***write next states for some random states in both cases***

## hamming Code (1bit error correcting code)

- steps
  - sender
    1. figure out the number of parity bits required ($2^p \geq m + p + 1$)
    2. make the structure for the encoded message
    3. form groups and find the value of parity bits
       1. parity bit = `xnor` of all message bits in its group
  - receiver
    - write all groups with parity bit
    - write 1 against group with even number of 1s
    - ***combined bits(in reverse) gives the position of the error***
- [ ] [Arbiter Practice](https://drive.google.com/drive/u/1/folders/1OZRbEKXlzcwTNG6a1cZO0YHb-327ovGH)
- [ ] ***practice 2 messages (with and without error)***

## CRC (cyclic redundancy check)

- divisor(generate) polynomial
- dividend(message) polynomial
- ***Encoded message: for a k-bit divisor select (k-1) bit from remainder and append to the end of dividend***
- additionally, there is an look-up table to find the position of bit

# Lecture 3

- sequential => involvement of clock

## Types of CRC implementation

### Combinational

<details>
<summary>Diagram</summary>

![](/assets/images/2022-11-21-14-27-22.png)

</details>

- separate hardware for separate stages
- each continuously driving values from previous ones
- we will get output in single cycle
  - but the delay will be very large (delay of 8 `XOR` gates)
  - might not be possible to connect with other components with large delay

### Iterative

- additional hardware is required
  - register to store the answer of previous stage
  - hardware for counter(kmap or adder)

#### Rolled Version

<details>
<summary>Diagram</summary>

![](/assets/images/2022-11-21-14-27-59.png)

</details>

- time period is small / frequency is high
- less `XOR` gates are required
- we have to wait for 8 cycles to get an answer

#### Unrolled Version

<details>
<summary>Diagram</summary>

![](/assets/images/2022-11-21-14-28-17.png)

</details>  

- pipelined version
- more `XOR` and flip-flops are required
- new input can be fed every cycle
- output is also obtained every cycle
  - initially -- we will have to weight for 8 cycles

### Setup Time in Flip-Flops (for iterative versions)

<details>
<summary>Diagram</summary>

![](/assets/images/2022-11-21-14-28-43.png)

</details>

- setup delay is common and is required for every
  - between rolled and combinational, combinational takes less time
    - combinational: $T_{clkq} + 8 * T_{xor} + T_{setup}$
    - iterative: $T_{clkq} + 8 * T_{xor} + 8 * T_{setup}$
  - ***still rolled is preferred, as frequency of combinational is very large and can cause problem in connecting***

- [ ] ***practice a sum on CRC***
- [ ] ***revise the names and comparison of 3 formats***

# Lecture 4

## LFSR (linear feedback shift register)

- uses: *random number generator*

- steps:
  - from the generic circuit, create `polynomial` specific circuit
  - 0 => short, 1 => keep xor gate
- example: $1 + x^2 + x^3 + x^4 + x^n$

### Standard Format

- next state equation
  - shift every bit to right
  - xor the ones with XOR gate before it

<details>
<summary>general</summary>

![](/assets/images/2022-11-21-23-12-07.png)

</details>

<details>
<summary>converted for example</summary>

- ![](/assets/images/2022-11-21-19-36-11.png)

</details>

### Modular Format

- next state equation
  - shift every bit to right
  - for LSB: xor MSB with registers having XOR gates before them

<details>
<summary>general</summary>

- ![](/assets/images/2022-11-21-19-34-34.png)

</details>

<details>
<summary>converted for example</summary>

![](/assets/images/2022-11-21-23-14-29.png)

</details>

#### Differences

- looking at the structures:
- in modular format, maximum delay is 1 `XOR` only
- in standard format, this delay can be larger(more than 1 `XOR`)

<blockquote style="background-color: #43b02a20; padding:3px 2px; border-radius: 5px; border-left: 0.25em solid #43b02a; padding-left: 0.75em">non-zero seed would not work</blockquote>

### LFSR based CRC

<details>
<summary>structure</summary>

![](/assets/images/2022-11-22-00-05-36.png)

</details>

<details>
<summary>example</summary>

![](/assets/images/2022-11-22-00-05-04.png)

</details>

- one additional `XOR` gate at the input
- steps
  - LFSR is initialized to all zeros
  - We keep passing a single bit, starting from the MSB of `msg` + `0_padded`
  - we update the LFSR values based on the equation(created using generate polynomial)

- [ ] ***derive specific circuit from general***
- [ ] ***derive equations and work out LFSR CRC***
