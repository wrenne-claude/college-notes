### Variables and literals
A **variable** may be understood as a named region of memory storing a value of a specified type. Each variable, before it can be used, has to be created (declared and defined) - in declaration we specify its name and type. It is also recommended to assign a value to any newly created variable (initialization). The java compiler will not allow us to refer to the value of a variable until it can see an assignment of a value to this variable. When assigning a value, we can use the value of any expression yielding a value of an appropriate type; in the simplest case this may be just a value specified literally.
A number written without a decimal dot is understood to be of type **int**
```java
int a = 7;
int b = a + 5;
```

For local variables, instead of declaring a type explicitly, one can use a special keyword **var**: then the compiler will figure the type out itself. Of course, we have to give it a chance to do so, so the variable being defined must be initialized. For example, the definitions above could have been written as
```java
var a = 7;
var b = a + 5;
```
because the initializers on the right tell the compiler that **a** and **b** should be of type **int**.

We can add a letter 'L' (or lower case 'l', but that could be easily confused with '1') at the end if we want the compiler to treat it as a **long**
```java
long m = 101L, n = 2147483648L;
```
Note that 2147483648 without the 'L' would be treated as an **int**, but that would be wrong, because it is too big for an **int**!

Literal integers may also be written in octal, hexadecimal or binary:
```java
int a = 189, b = 0275, c = 0xBD, d = 0b10111101
```

---
### Chars
As **char** is a numerical type, the value will be a number, namely the Unicode code of a given character (which for 'A' is 65). As **char** occupies two bytes and is treated as a non-negative number, its values are in the range $[0, 2^{16}-1] = [0, 65535]$ which is enough for all letters (and other symbols) in almost all languages to be represented. Characters that are not present on our keyboard may be entered like this: `{java icon} char c = '\u03B1';`. In this case, the code `0x03B1` corresponds to the Greek letter $\alpha$. There are also some special characters that cannot be entered from the keyboard, like CR (carriage return), LF (line feed), etc.
They can be specified using the Unicode notation, as above, but they also correspond to special symbols

Some examples of literals can be found in the program below:
```java title:Literals.java
public class Literals {
	public static void main(String[] args) {
		System.out.println(22);             // decimal
		System.out.println(022);            // octal
		System.out.println(0x22);           // hexadecimal
		System.out.println(0b1001);         // binary
		System.out.println(22.22);          // double
		System.out.println(2.22e-1);        // "scientific"
		System.out.println(1/3 );           // this is 0 !
		System.out.println(1/3.);           // one third
		System.out.println(1/3D);           // 3D -> double
		System.out.println('A');            // char
		System.out.println('A'+2);          // char
		System.out.println((char)('A'+2));
		System.out.println('\u0042');       // also char
		System.out.println("Hello, World!");
		System.out.println("\u017b\u00F3\u0142w");
		System.out.println("number = " + (2+2));
		System.out.println(false);
		System.out.println("\"TAB\"s and 'NL'\n"+
		                   "a\tb\tc\te\tf\n\tg\th\ti\tj");
		System.out.println("C:\\Program Files\\java");
	}
}
```
The file's output should be the following:
```
22
18
34
9
22.22
0.222
0
0.3333333333333333
0.3333333333333333
2147483648
-2147483648
2147483648
A
67
C
B
Hello, World!
Żółw
number = 4
false
"TAB"s and 'NL'
a    b    c    e    f
     g    h    i    j
C:\Program Files\java
```

---
### Conversions
Sometimes a value of one type should be used as a value of another type. Creating a value of one type based on a value of another type is called **conversion** or **casting**. Of course, it is impossible to change the type of a variable, as conversions always involve values.
For example, in
`{java icon} int a = 7;`
`{java icon} double x = a + 1;`
the value of the right-hand side in the second line is of type **int** and a **double** is needed to initialize the variable x; however, the compiler will silently convert **int** value to the corresponding **double** value and assign it to x. Such conversions, performed automatically by the compiler, are called **implicit conversions**. Generally, they will be performed if they don't lead to a loss of information.
Conversion in the opposite direction
`{java icon} double x = 7.7;`
`{java icon} int a = x; // WRONG`
will *not* be performed; the snippet above wouldn't even be compiled.
This is because an **int** occupies four bytes and has no fractional part, while doubles do have fractional parts and occupy eight bytes. Hence, conversion from **double** to **int** would lead to inevitable loss of information. We can, however, enforce the compiler to perform such conversions (taking the responsibility for possible consequences).
We do it by specifying, in parentheses, the name of the type we want to convert to:
`{java icon} double x = 7.7;`
`{java icon} int a = (int)x; // now OK`
Of course, after the conversion, **a** will be exactly 7, as there is no way for an **int** to have a fractional part.

***Note:** this conversion does not affect the variable **x** as such: its type is still **double** and its value is still 7.7.*

The exact rules of conversions are more complicated, but the general principle is that conversions from "narrow" types to the "wider" ones are performed implicitly:
**byte**, **char**, **short** --> **int**, **int**, **float**, **long** --> **double**, etc.,
while conversions in the opposite direction must be explicit.

---

### I/O

```java title:ReadKbd.java
import java.util.Scanner;
import java.util.Locale; // see below

public class ReadKbd {
	public static void main(String[] args) {

		// If the locale is set to Polish, floating point numbers
		// have to be entered with a comma as the decimal separator.
		// The locale can be changed to American by uncommenting
		// the line below:
		
		// Locale.setDefault(Locale.US);
		
		// Now the dot will be used as a decimal separator.
		// When reading data, any nonempty sequence of white
		// characters is treated as a separator.
		
		Scanner scan = new Scanner(System.in);
		
		System.out.println("Enter an int, a string and two doubles");
		int k = scan.nextInt();
		String s = scan.next();
		double x = scan.nextDouble();
		double y = scan.nextDouble();
		// scan.close(); //don't close if reading from System.in
		System.out.println("\nEntered data:\n\nint = " +
			k + "\nString = " + s + "\ndouble1 = " + 
			x + "\ndouble2 = " + y + "\n");
	}
}
```


