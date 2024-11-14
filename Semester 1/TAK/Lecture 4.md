## Digital Circuits
#### Combinational circuit
Input signal ($X_{1} ... X_{n}$) specifies output signals ($Y_{1} ... Y_{m}$)
#### Sequential circuit
In a sequential circuit, output signals depend on the input signals, as well as on the previous input states (sequence). Sequential circuits also remember previous states
#### Digital circuits:
+ Gates
+ Flip-flops
+ Registers
+ Counters
+ Encoders/Decoders
+ Adders (Summers)
+ Comparators
+ Multiplexers/Demultiplexers
+ Pulse generators

---
## Logic gates
Truth table:

| A   | B   | AND | NAND | OR  | NOR | XOR | XNOR |
| --- | --- | --- | ---- | --- | --- | --- | ---- |
| 0   | 0   | 0   | 1    | 0   | 1   | 0   | 1    |
| 0   | 1   | 0   | 1    | 1   | 0   | 1   | 0    |
| 1   | 0   | 0   | 1    | 1   | 0   | 1   | 0    |
| 1   | 1   | 1   | 0    | 1   | 0   | 0   | 1    |

---
## Flip-Flops
#### RS flip-flop
on NAND gates (the active state is 0)

| $^{-}R$ | $^{-}S$ | $Q_{n+1}$ |
| ------- | ------- | --------- |
| 0       | 0       | -         |
| 0       | 1       | 0         |
| 1       | 0       | 1         |
| 1       | 1       | $Q_{n}$   |

on NOR gates (the active state is 1)

| R   | S   |
| --- | --- |
|     |     |

#### D flip-flop
It is a synchronous flip-flop. The change in the state of the flip-flop occurs under the influence of the change of the clock signal C from 0 to 1. At the moment the signal given to the information input D is remembered.

#### T flip-flop
When the value of 1 is applied to the input of the T circuit, it changes to the opposite state with each falling slope of the clock signal. When you specify **o** for input, it does not change the state

#### JK flip-flop
After giving the appropriate values for the information inputs J and K of the system, it changes the state to the opposite at each falling slope of the clock signal.

---
## Registers
A registry is a circuit used to store digital information.
It occurs as a functional block in almost all major digital devices.
The essential element of the register is a flip-flop, which allows you to remember one bit of digital information.
Parameters characterising the register:
+ n = length of the register = number of flip-flops
+ The capacity of the registry is equal $2^{n}$ and specifies the maximum amount of different information that can be stored in the registry.
+ Registry speed:
	+ For a serial register --> the maximum frequency of clock pulses at which the movement of the combination is not distorted.
	+ For the parallel register --> time of input and output of information
#### Parallel
Allows parallel entry and output of information simultaneously to all and from all entries in the register
#### Serial
Allows serial input and output of information, i.e. bit by bit
#### Serial-parallel
Allows serial input and parallel output of information
#### Parallel-serial
Allows parallel input and serial output of information

---
## Counter
+ If the counter after reaching the last state in the cycle is to have again **S** of distinguishable states, it should be reduced to the **initial state**
+ The number of states that a counter takes in a full cycle is called the **cycle length** or **counter capacity**
+ Counters can be **unidirectional** or **bidirectional** (reversible)
+ Unidirectional counters are divided into forward counting and backward counting counters
---
## Encoders/Decoders
**Encoder** - it is a circuit n/m (number of inputs/outputs) used to convert code 1 from n (ring) to another code (e.g. binary)
**Decoder** - a circuit n/m (number of inputs/outputs) used to convert code (e.g. binary) to code 1 of n
Code **1 of n** has **n** inputs, with the 1 as the highlighted state
Code **0 of n** has **n** inputs, with the 0 as the highlighted state

Encoders are mainly used to enter information in the form of decimal digits

---
## Adder
Adding binary numbers can be done in series or parallel, hence we have serial or parallel adders.

| A   | B   | C   | S   |
| --- | --- | --- | --- |
| 0   | 0   | 0   | 0   |
| 0   | 1   | 0   | 1   |
| 1   | 0   | 0   | 1   |
| 1   | 1   | 1   | 0   |
#### Serial adders
In each tick of the clock, two bits of components from the corresponding positions and a transfer bit from the previous position are added, starting from the least significant position.
The transfer from the previous position is remembered using flip-flop D.
#### Parallel adders
The advantage of the parallel adder is the high speed of operation, and its huge disadvantage - complexity (a large number of adders).

---
## Comparators
+ **Comparators** are used to compare the values of two or more binary numbers
+ The simplest comparators determine whether the compared numbers A and B are equal, e.g. A = B
+ More complex systems are comparators that determine which of the compared numbers is larger, e.g. A > B
+ It is often required that the comparator defines three possibilities, i.e. A > B, A = B, A < B
+ Comparators can be implemented as serial or parallel circuits
#### Serial comparators
The inputs of the serial comparator are given and compared to the subsequent bits of the two components

If we compare two positive numbers starting from the **most significant bit,** the **largest number** is the number with the **larger first bit.**

When the comparison is made starting from the **least significant bit,** the **larger number** is the one with the **larger last bit.**

---

## Multiplexers/Demultiplexers
A **multiplexer** is a logic circuit that allows data to be sent to the output of the one from the signals fed to the information input, which is led to the input with the number specified by the address inputs.
A **demultiplexer** is a logic circuit used to transfer data from one input to one of the many outputs of a selected address.

Input numbers are presented in a natural binary code.
#### Pulse generators
Circuits that generate a pulse of a particular duration, under the influence of a triggering pulse.

---
## Integrated circuits
A miniaturized electronic circuit performing a specific function, containing from several to hundreds of millions of basic electronic components, such as transistors, resistors, diodes, etc.

#### Scales:
+ SSI - Small Scale of Integration - up to 100 elements
+ MSI - Medium - 100-1000
+ LSI - Large - $10^{3} - 10^{5}$
+ VLSI - Very Large - over $10^{5}$
+ ULSI - Ultra Large - over $10^{6}$
**Parameters characterizing integrated circuits:**
+ Propagation time - the time elapsed from the moment of changing the input state of the logical system to the moment of changing the state of outputs, which is a reaction to this change in input
+ Power loss
	+ Interference immunity
	+ Load capacity -  determines how many inputs of other systems can be connected to the output
