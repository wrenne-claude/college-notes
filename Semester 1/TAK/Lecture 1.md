### Computer Techniques and Architecture
+ History and development of computer science, basic concepts, abstraction levels of description of computer systems, the idea of architecture and architectural models
+ Logic, numeric notations, representation of constant and floating point notation
+ Basic digital circuits, logic ops, sequential and combination digital circuits,
+ Data handling
+ Overview of components and their characteristics
+ Computer I/O chips
+ Modern computers, quantum computers, computer networks, neural networks in the context of a computer
### Lit.
1. ***Computer science: An overview* - J. Glenn Brookshear**
2. ***Fundamentals of Computer Organization and Design* - S. P. Dandamundi**
3. *Computer Architecture and Organization: Fundamentals and Architecture Security* - von Shuangbao Paul Wong
4. *A practical Introduction to Computer Architecture* - Daniel Stephen Page

#### Exam
+ Theoretical and practical knowledge
+ Presentation - +5% of the exam points

## The history
+ **Generation 0** - before the advent of universal, electronic digital machines
	+ 1935 - **J. Atanasoff** - binary computer design
	+ 1936-42 - **K. Zuse** - Z1, Z2, Z3, mechanical-electrical-relay construction, Z3 computer controlled with perforated tape, 8-bit instructions.
	+ 1937-44 - **Harvard Mk. I** - electromechanical calculator with data memory
+ **Generation 1** - computers built based on vacuum tubes
	+ 1945 - **ENIAC** (Electronic Numerical Integrator and Computer)
		+ The first computer build on vacuum tubes
		+ 0.1 MHz clock speed
		+ The program running on the computer was set with wires and switches, 20 registers
+ **Generation 2** - computers built based on transistors
	+ 1957 - NCR, RCA - the first transistor computers
	+ 1957 - DEC - the first transistor minicomputer PDP-1
	+ 1960 - IBM - transistor computers 7090 with magnetic core memory RAM
+ **Generation 3** - computers built based on small or medium-scale TTL integrated circuits
	+ 1964 - IBM - the first computer series IBM System 360
	+ 1971 - Intel - 4-bit microprocessor Intel 4004
	+ 1972 - Intel - 8-bit microprocessors Intel 8008 and Intel 8080
	+ 1975 - DEC - PDP-8/A microcomputer with solid-state memory and floating point processor
+ **Generation 4** - computers build based on high-scale integration of microprocessors
	+ 1978 - Intel - 16-bit micro
	+ 1980 - Berkeley Uni - RISC I and II
	+ 1981 - IBM -personal computer IBM PC XT
	+ 1983 - Intel - 16-bit micro Intel 80286 used in the IBM PC AT personal computers
	+ 1985 - Intel - 32-bit microprocessor Intel 80386, external cache and floating-point coprocessor
+ **Generation 5** - computers built based on unconventional solutions
	+ 1989 - Intel - Intel 32-bit microprocessors
	+ 1998 - Japan, the first RISC microprocessor with a clock speed of 1GHz
	+ 2000 - IBM, the first dual-core processor - IBM Power4
	+ 2002 - Intel - Pentium 4
	+ 2005
		+ Intel
		+ AMD
	+ 2010 - 6-core Intel Core
	+ 2020 - AMD - AMD Ryzen 7, up to 4.2 GHz
	+ 2022 - Intel - Intel 4 (7nm), Intel 3

**Litography** - more transistors per certain area. E.g. 7nm distance between transistors

### Moore's Law
It's a law formulated in 1965 by Gordon Moore, which in its original form says that the number of transistors in an electrical system doubles every year (in 1999, Moore decided that doubling would occur every 4-5 years).
+ Accurate until ~10 years ago
+ Not really a law, more of a speculative theory
### Landauer's principle
Erasing one bit of information in an environment with temperature **T** requires a loss (dissipation) of energy (or heat release) of at least **kT ln2**, where k is the Boltzmann constant.

### Limitations - Physics
The average distance of silicon atoms is 0.25nm
+ For lithography 2.7um number of atoms along the side of the gate = 10 000
+ For 27nm lithography, the number of atoms along the side of the gate is only 100
+ With the current **7nm** lithography technology, the number of atoms along the side of the gate is around 26

+ Dielectric strength of silicon dioxide - 5 MV/cm
+ For 27nm lithography - maximum voltage approx. 13,5V
+ For 10nm lithography - max. volt. approx. 10V
+ For 7nm lithography - max. volt. approx. 3.5V
+ For 5nm lithography - max. volt. approx. 1.5V

### Abstraction levels
+ Software
+ Operating system
+ Architecture
+ Microarchitecture
+ Logical level
+ Digital circuit level
+ Analog circuit level
+ Electronic level
+ Physics

## Computer Architecture
**What is computer architecture?**
+ How to organize the elements that make up your computer
+ According to the definition given in 1964 by **G. Amdahl**:
	+ *Computer architecture is a characteristic of a computer that a programmer must know to write a valid program in the internal language for that computer.*
##### Exo-architecture
+ Devices shall be treated as components of the scheme and their functional description shall be given
##### Endo-architecture
 + Devices are described at a lower level of abstraction (more detailed) than at the exo-architecture level. Not only the scheme and properties are described, but also the operation of the elements of this scheme.
---
+ SISD - *Single Instruction, Single Data*
+ SIMD - *Single Instruction, Multiple Data*
+ MISD - *Multiple Instructions, Single Data*
+ MIMD - *Multiple Instructions, Multiple Data*
---
+ CISC - *Complex Instruction Set Computer*
	+ A relatively large number of predefined commands/instructions - several hundred
	+ The occurrence of complex, specialized instructions
	+ Low optimization
	+ Lower CPU clock speed than RISC
	+ A large number of modes for addressing instructions
	+ Unlike RISC, instructions can operate directly on memory (instead of sending values to and working on registers)
	+ The command decoder is complicated
+ RISC - *Reduced Instruction Set Computer*
	+ The number of orders reduced to the necessary minimum - several dozen
	+ Reduction of addressing modes, making command codes simpler and more unified, which further simplifies the command decoder
	+ Limitation of memory-processor communication
	+ Increasing the number of registers also has the effect of reducing the number of memory references
	+ Modern processors, from the programmer's point of view, are typically CISC processors. Still, RISC commands are broken down into processor micro-commands and executed by the RISC core: CCR Architecture (CISC-core-RISC) execution block
+ CCR - *CISC-core-RISC*

Architectures can also be classified according to the way memory is organized and the program is executed:
+ Von Neumann Architecture
	+ A.K.A. Princeton Architecture
	+ Common memory for both data and program code
	+ Allows you to auto-modify the program
	+ Excludes simultaneous retrieval of instructions and operations on data
+ Harvard Architecture
	+ Separate program and data memory
	+ Allows you to retrieve instructions and perform operations on data simultaneously
	+ In the original model representation, it appears in the controllers
+ Mixed Architecture
	+ AKA Harvard-Princeton
	+ Separate program and data memory at the cache level
	+ Both memory areas use common buses
	+ High performance for simultaneous instruction retrieval and data operations
	+ Used in most modern processors