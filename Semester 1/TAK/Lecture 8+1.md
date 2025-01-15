Microprocessor system structure
## I/O operations
Input/Output operations are needed to exchange data between a microprocessor and memory, and an external device.

A distinction is made between operations with:
+ direct control by microprocessor
+ indirect control by microprocessor

Input/Output operations with indirect microprocessor control are performed using a special direct memory access circuit (DMA)
#### Direct control by microprocessor
**Operations with direct microprocessor control (PIO)**
**P**rogrammed **I**nput/**O**utput

Input/Output operations with direct control by the microprocessor are characterized by data being transferred between the microprocessor register and the I/O register as a result of the microprocessor commands executing

I/O devices <==> Processor <==> RAM

#### Indirect control by microprocessor
**Operations with indirect microprocessor control (DMA)**
**D**irect **M**emory **A**ccess

The direct memory access chip is used for transmission between an external device and the main memory.

Data exchange occurs between a specific area of RAM and an external device, bypassing the microprocessor.

## Cooperation of the central unit with external devices
### Types of transmission
Types can be divided into categories due to:
+ **Transmission direction**
	+ One-way transmission
	+ Alternating transmission
	+ Simultaneous transmission
+ **How each bit is transmitted**
	+ Serial transmission
	+ Parallel transmission
+ **How data is transferred over time**
	+ Synchronous transmission
	+ Asynchronous transmission
## Computer expansion buses
The modular design of computers allows them to be expanded according to the user's needs
Peripherals whose primary drivers are not built into the motherboard require separate cards to be installed in the expansion slots

We distinguish the bus extensions of the computer into two different sets:
+ External buses (clocked with their separate clock)
+ Local buses (clocked at the frequency determined by the system clock)