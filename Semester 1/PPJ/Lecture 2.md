Binary - greatest possible integer:
0b+0 <- positive number + 31 ones (32 character limit) - $127_{10}$
smallest possible byte 1000 0000 ... 0000

how to write that greatest possible integer more efficiently than typing 31 ones?
`int a = 0x7FFFFFFF;` - write it in hexadecimal
what about the smallest possible integer?
`int b = 0x80000000;`

An operator - a symbol of operation (a plus, minus for addition and subtraction)
An operator needs 2 (or more?) operands

unary minus acts on one operand (negative sign)

If we have two integer numbers (we will use only eight-bit numbers for simplicity), we can AND them: the result will be a sequence of bits where there is 1 whenever there is 1 in both numbers at the corresponding position, and 0 otherwise - we can interpret it as the logical conjunction bit-by-bit with 1 corresponding to true and 0 to false:

`0 1 1 0 1 1 0 0` 
`0 1 0 1 0 1 0 1`
$=$
& `0 1 0 0 0 1 0 0`
So 108 & 85 = 

We can OR the numbers as well:
`0 1 1 0 1 1 0 0` 
`0 1 0 1 0 1 0 1`
$=$
| `0 1 1 1 1 1 0 1`
So 108 | 85 = 125

Or XOR (exclusive OR) them:
`0 1 1 0 1 1 0 0` 
`0 1 0 1 0 1 0 1`
$=$
^ `0 0 1 1 1 0 0 1`
So 108 ^ 85 = 57

Legend:
	AND = "&"
	OR = "|"
	XOR = "^"


If we XOR the result with 0s, the number will be exactly reproduced. So XORing with 1 flips the bit, and XORing with 0 leaves it intact. XORing with any bit with the same bit-value *twice* always reproduces the original value.

**Unary operations** - such operations that affect just one operand
Negation (NOT, symbol - `~`) - flips all bits
~ 01101100 -> 10010011

Shifting - << or >>

### Floating point types
The representation of floating point numbers (that represent real numbers known from mathematics) is completely different. Let us consider **float** (although it is not much used). Numbers of this type are stored in 4 bytes, i.e., 32 bits. The highest bit is just the sign bit: 0 for positive values, 1 for negative. Then we have eight bits of the so called exponent, and 23 bits of the mantissa.

seeeeeeeefffffffffffffffffffffff

Eight bits of the exponent are collectively denoted by E and described by the number from the range [0, 255] that these eight bit represent in the binary system. The 23 bits of the mantissa are denoted collectively as F.

### Object types
Besides primitive types, there are also the so called **object types**. They are defined by the user, although many such types are already defined by implementers of the standard library and we can use them in our programs. Names of object types should always start with an upper case letter (it's not enforced by the compiler, but is a convention we should always observe).
Objects of these types (variables) cannot be created locally on the stack and never have names. They are created on the heap and can be automatically removed from memory when not needed anymore. We have access to such objects only through references (pointers) to them which physically contain only their addresses, not values. There is a special process, called **garbage collector**, which detects objects on the heap which are not referenced anymore by any reference variable in the program and removes the unnecessary objects from the memory.

### Variables
When assigning a value to a variable, we can use the value of any expression yielding a value of an appropriate type; in the simplest case this may be just a value specified literally. A number written without a decimal dot is understood to be of type **int**.
`int a = 7;`
`int b = a + 5;`

For local variables, instead of declaring a type explicitly, one can use a special keyword **var**: then the compiler will figure the type out itself. Of course, we have to give it a chance to do so, so the variable being defined must be initialized. For example, the definitions above could have been written as
`var a = 7;`
`var b = a + 5;`


We can add the letter L (preferably uppercase) at the end of an int if we want the compiler to interpret it as a **long**.
