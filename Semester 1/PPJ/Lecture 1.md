+ Only **one** retake

#### Bits and bytes, hexadecimal and octal system
+ Bit: the smallest unit of information
+ Byte: a sequence of 8 bits
	+ There are 2^8 = 256 such sequences possible; interpreted as numbers in the binary system, they assume values in the closed intervals [0, 255]
	+ For example IP addresses, their numbers are between 0 and 255
	+ RGBa colors are also expressed by numbers between 0 and 255
	+ Signed integers - we can interpret the interval as divided into two parts - negative and positive
+ Hexadecimal notation: It follows that there is a one-to-one correspondence between all possible bytes and all sequences of exactly two hex-digits. 
	+ One-to-one correspondence between any sequence of four bits and a single digit in hexadecimal notation
	+ Four bits can be 2^4 = 16 combinations
	+ 0-9, A, B, C, D, E, F - hex-digits A-F can also be written in lowercase
	+ 255`10` = 11111111`2` = FF`16` and 46`10` = 00101110`2` = 2E`16`
+ Decimal vs. Binary
	+ When reading a number written in decimal digit-by-digit from right to left, we treat each digit as [digit] * [10 to the power of x], where x starts at 0 and raises by 1 with each digit
		+ 372 = 2 * 10^0, 7 * 10^1, 3 * 10^2.  
	+ When reading a number written in binary digit-by-digit from right to left, we treat each digit as [digit] * [2 to the power of x], where x starts at 0 and raises by 1 with each digit
#### Processor
+ Registers - information, in the form of sequences of bits, can be stored there and manipulated by **instructions**, which themselves are also expressed as sequences of bits.
+ There is a limited number of instructions that any given processor 'understands' (its **instruction set**). These are elementary instructions, like 'set register X to value...', 'copy data from a memory location M to register Y' (or vice versa), 'add (subtract, multiply, divide) the values of two registers', etc.
+ No matter what programming language we use, our program must be ultimately somehow transformed into the form of a long sequence of these simple, elementary instructions (i.e. into the form of **machine code** or **executable**)
#### Program
+ Sequences of instructions (perhaps from many source files) in any language which, after transforming into machine code, performs an indicated task.
#### Compiler
+ A program which reads one or more source files (just text files) and transforms them into machine code which can then be passed to the processor. Sometimes the result is not an executable, but has some intermediate form, which is then compiled 'to the end' and passed to the processor by another, additional program. This, for example, is the case for Java.
+ Some languages aren't compiled (interpreters are used)

## What is Java?
Java is a high level imperative programming language, object-oriented with some elements of functional programming. In the design of Java, emphasis has been put on
1. platform independence;
2. simplicity;
3. safety (no direct access to memory, as in C/C++, garbage collector, managing security issues, etc.);
4. efficiency;
5. very rich standard library.

##### Some features of Java:
1. Designed with commercial use in mind by Sun (James Gosling, mid-90s)
2. Compiled to platform independent byte code.
3. Executed by (platform *dependent*) JVM - Java Virtual Machine, which interprets byte code, transforms it into machine code (dynamically, without storing on a disk) which is passed to the processor(s)
4. Simple syntax, very close to that of C/C++
5. Built-in (in the form of a platform independent standardized library):
	+ graphics (building GUIs - graphical user interfaces);
	+ multithreading (concurrency);
	+ network programming;
	+ working with databases;
	+ multimedia (processing images and sound);
	+ support for various security issues;
	+ support for *microprogramming* - for 'small' devices, mobile phones, etc.
	+ handling various data formats, like XML, JSON, etc.;
	+ ...and much more
#### Installation:
Install the JDK (Java Development Kit) - *(preferably from Oracle)* it installs the JVM (allowing to run Java programs), but also various tools allowing the developer to create Java programs (in particular, the compiler)
The documentation is available as one big zip file, but can also be viewed online.


### Types, variables, literals
#### Primitive types
Any piece of data must have a **type**. In Java, the types that may correspond to named variables are called **primitive** (or fundamental) types. We may think of a **variable** of a primitive type as of a named piece of memory containing a single value of a well defined type. The type of a variable determines its length (number of bytes it occupies) and the way its contents are interpreted. In Java, only variables or primitive types can be created locally, on the stack - objects of all other types can only be created on the heap (free memory) and never have names (identifiers).

#### Identifiers
Identifiers in Java may be of any length and may consist only of:
+ Letters - can be lower- or upper-case. Lower and uppercase letters are considered different, 'a' and 'A' are **not** equivalent. In principle, all letters, in any language, can be used, but it's recommended to stick to Latin letters only.
+ Digits - they **cannot** appear at the beginning of any identifier. As with letters, any characters considered to be digits in UNICODE may be used, but in practice we use only Arabic digits.
+ The underscore character (' _ ')
+ Currency symbols (such as $).

There are several conventions concerning identifiers which are generally accepted and should be followed:
+ Only the names of classes and interfaces should start with a capital letter
+ If a name consists of several words, the first letter of each internal word should be capitalized (the so-called *camel-case notation*). For example, `getWidth`, `setCurrentRate`, etc.
+ The names of variables declared as constants should be all uppercase with words separated by underscores (e.g., `MIN_WIDTH`).

Some names are used in Java as the so-called **keywords**. They have special meaning in the language itself (and do not correspond to nay variables or classes). These names are reserved and *cannot* be used as identifiers of anything.

#### Overview of primitive types
+ ##### Numerical types:
	+ Integral types correspond to integer (whole) numbers. Their possible values belong to the interval [-2^N-1, 2^N-1 - 1], where N is the number of bits (one byte = 8 bits). The exception is **char** whose values are always interpreted as non-negative and belong to interval [0, 2^16 - 1].
		+ **byte** (1) - values in range [-128, 127];
		+ **short** (2) - values in range [-32768, 32767];
		+ **char** (2) - values in range [0, 65535] interpreted as Unicode code points of characters (always non-negative);
			+ Displayed as a **character** (hence the name), so for example 65 will be displayed as 'A'.
			+ There's also Unicode codes for non-English characters, such as unique Polish or German letters.
			+ It's not just for letters and digits, there's also symbols of planets, emojis, playing card symbols and so on.
		+ **int** (4) - values in range [-2.147.483.648, 2.147.483.647];
		+ **long** (8) - values in an astronomical range
	+ Floating point types correspond to real numbers (with fractional parts). There are two such types with different ranges and precision.
		+ **float** (4) - values in range [~ 1.4 * 10^-45, ~ 3.4 * 10^+38] positive or negative, with roughly 7 significant decimal digits - rarely used;
		+ **double** (8) - values in range [~ 4.9 * 10^-324, ~ 1.8 * 10^+308] positive or negative, with roughly 16 significant decimal digits.
+ ##### Logical type boolean:
	+ It has only two possible values: **true** and **false**. They are *not* convertible to numerical values, neither are numerical values convertible to **boolean** (as they are in many other languages);
	+ Purely technically it could be represented by a bit (2 values), but that's not the case.
+ ##### Reference to objects:
	+ Variables of these types hold as their values *addresses* of objects (of the so-called object types, there are no references to variables or primitive types in Java). 
	+ In C/C++ such variables are called **pointers**.
#### Integral types
A **byte** contains 8 bits, so we can represent it by a sequence of eight digits, each of which is 0 or 1
`b7b6b5b4b3b2b1b0`
This can be interpreted as a number in the binary system, so consecutive digits (from the right) are coefficients at consecutive powers of 2. There is a quirk, however: in order to be able to represent also negative numbers, the term with the highest power of 2 is taken with negative sign
`-b7 * 2^7 + b6 * 2^6 + b5 * 2^5 ...`
So the leftmost digit decides whether the number is positive or negative. A '0' would mean we don't want a negative leftmost digit, therefore the number would be positive.

0x = "interpret in hexadecimal"
when put in front of a number, it lets the compiler know that the following digits should be interpreted as a hexadecimal number

0 at the beginning = "interpret in octal system"

0b = "interpret in binary"

`27 = 27`
`0x27 = 39`
`027 = 23`
`0b1101 = 33`

0111 - positive - `7` in decimal
1000 - negative - `-8` in decimal

greatest possible number in hexadecimal:
0x7FFFFFFF
(can use at most 8 characters after the 0x)
smallest possible integer in hexadecimal:
0x80000000