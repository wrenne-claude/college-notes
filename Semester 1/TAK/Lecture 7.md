## Structure of the microprocessor system
#### Arithmometer section
+ **Arithmometer - ALU (Arithmetic and Logic Unit** - performs arithmetic and logical operations
+ **Accumulator -** contains one of the operation's arguments and is also where the result of the operation is stored
+ **Flag register -** there is stored information about the results of ALU operations
#### Control section
+ **Command register -** used to remember the command code retrieved from memory
+ **Command decoder -** used to decode the command, allowing the control unit to generate the appropriate control signals
+ **Control unit -** ensures the correct sequence of events in the system.
By generating the right signals, the control unit:
+ determines the type of operations performed by the ALU
+ controls the work of all microprocessor registers
+ controls the transmission of information
+ sends control signals to external devices
#### Registry section
+ **General Purpose Registers -** used to store frequently used arguments, access to which should be as quick as possible
+ **Stack Pointer -** used to address the stack memory cell (the fragment of memory into which the contents of the registers are entered when they move to execute another program)
+ **Program Counter -** indicates where the next commands are stored in memory
+ **Address Register -** indicates the memory cell in which the command/data byte is located or the cell to which the data byte should be written
![[Pasted image 20241113155732.png]]
## CPU clock frequency
The frequency depends on the oscillator made of quartz crystal. After connecting the power supply, the quartz begins to vibrate. The frequency of these vibrations depends on the shape of the quartz.

Performing any operations by the processor takes place in a certain order in subsequent periods of time. The shortest segment is a single cycle. Each CPU activity requires at least one, and most often more, cycles.

The unit of frequency is Hertz (Hz).

#### Internal registers
The size of internal registers determines the amount of information that a processor can process per one unit of time.
## Cache
The operating memory is slow (long access times). To speed this up, a **cache** is used. It is a static memory with short access times, but it is unfortunately very expensive, so a compromise has been created - a large and cheap main memory supported by a fast cache.

For memory operations, the cache driver checks to see if the data is in the cache.
+ If so, the operation is performed on the cache memory - "cache hit".
#### Cache types
+ **L1** - located inside the processor, closest to the main CPU kernel and enables the fastest communication
+ **L2** - used when the first is occupied
+ **L3** - used when L2 is insufficient to hold the necessary data
#### Cache topologies
+ Look-Aside (cache attached parallel to the memory bus)
	+ ![[Pasted image 20241113161646.png]]
+ Look-Through (cache memory is connected to the main memory)
	+ ![[Pasted image 20241113161619.png]]
+ Look-Backside
	+ ![[Pasted image 20241113161841.png]]

## Processor Enclosures
+ DIP - Dual In Package Line
	+ SEC (Single Edge Cartridge)
		+ The processor together with the cache chips is places on the expansion board, which is placed in the motherboard slot
	+ PLCC (Plastic Leaded Chip Carrier)
		+ The case is most often used in flash memory with BIOS on motherboards. These types of integrated circuits can be mounted in a socket
	+ PGA (Pin Grid Array)
		+ a set of pins on the nodes of the square grid
		+ SPGA (Staggered PGA) - modification in which the pins are additionally placed inside the mesh of the square grid
		+ ZIF (Zero Insertion Force) stands with zero clamping force are currently used to avoid damage during installation/replacement
	+ BGA (Ball Grid Array)
		+ The type of enclosure used in surface mounting technology
	+ LGA (Land Grid Array)
		+ In the processor, instead of pins, contact fields were introduced. In the socket, elastic plaques are touching these fields
	+ TCP (Tape Carrier Package)
		+ Housing in which electronic circuits in the form of copper are applied to a flexible foil material (tape-laminate)