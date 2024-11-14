## Switch statements and expressions
There are two kinds of switch instructions in Java. First, let's consider the *classic* form of this instruction, the **switch statement.** It resembles a series of **else if** statements (but is not equivalent!!!).
```java
switch (expr) {
	case val1 :
		statement1;
		// ...
		statementN;
		break;
	case val2 :
		statement1;
		// ...
		statementN;
	// ...
	default:
		statement1;
		// ...
		statementN;
		break;
}
```
+ **expr** (the so-called *selector*) must be parenthesized and be of an integral type (but not **long**), or one of the corresponding boxed types (**Int**, **short**, etc.), or the reference to a **String**, or an enumeration constant.
+ **val** stands for values with which the value of **expr** will be compared (in the specified order). They have to be literal values (not variables). If the value of **expr** is equal to any of the **val**s, the code in the corresponding arm is executed, and then the execution falls through (continues) with all the arms below.
+ Normally, that *falling through* is not what we want, so to avoid it, we use **break,** which transfers control flow out of the **switch** block (sometimes this *falling through* may just be what we want).
+ At the end of the example, the **default** arm is used, where no comparisons are made - this will be the arm that's selected if all other comparisons yield **false.** The **default** clause is optional and doesn't have to appear as the last(!).

The following example shows how to find a numerical value of a hex digit.
Here we take advantage of the *falling through* feature; note that if **ch** is any lower case letter from the range [a,f], due to *falling through*, we will end up in line 24 and then break out. The same applies to digits:
```java title:Switch.java
import java.util.Scanner;

public class Switch {
	public static void main (String[] args){
		Scanner scan = new Scanner(System.in);
		System.out.print(
			"Enter a single hex digit -> ");
		char ch = scan.next().charAt(0);
		
		// toLower by hand
		if (ch >= 'A' && ch <= 'Z')
			ch = (char)(ch + 'a' - 'A');
		
		int num;
		
		switch (ch) {
			case 'a':
			case 'b':
			case 'c':
			case 'd':
			case 'e':
			case 'f':
				num = 10 + ch - 'a';
				break;
			case '0':
			case '1':
			case '2':
			case '3':
			case '4':
			case '5':
			case '6':
			case '7':
			case '8':
			case '9':
				num = ch - '0';
				break;
			default:
				num = -1;
		}

		System.out.println("Character '" + ch + "' is " + 
			(num >= 0 ? "" : "not ") + "a hex digit. " + 
			"Its numerical value: " + num);
	}
}
```

Instead of the colon, we can use the "arrow" ('->') symbol. When we do,
+ *Falling through* is "turned off";
+ to the right of the arrow, we can put:
	+ a single statement or expression
	+ a block (enclosed in braces)
	+ a **throw** statement
For example in the following code, we don't use any **break** statements:
```java title:SwitchArrow.java
import java.util.Scanner;

public class SwitchArrow {
	public static void main(String[] args){
		Scanner scan = new Scanner(System.in);
		System.out.print(
			"Enter a natural number -> ");
		int k = scan.nextInt();
		
		String part1 = k + " is of the form ";
		String part2 = null;
		
		switch (k % 4) {
			case 0 -> part2 = "4n";
			case 1 -> part2 = "4n+1";
			case 2 -> part2 = "4n+2";
			case 3 -> part2 = "4n+3";
			default -> {
				part 2 = " ... probably negative";
				System.out.println("You were expected to " + 
					"enter a *natural* number!");
			}
		}
		System.out.println(part1 + part2);
	}
}
```

One can also supply more than one values (comma separated) in one arm of the **switch**
```java title:SwitchMult.java
public class SwitchMult {
	public static void main(String[] args) {
		String n = "BMW", country = null;
		switch (n) {
			case "BMW", "Opel", "Audi" -> country = "Germany";
			case "Peugeot", "Citroen"  -> country = "France";
			default                    -> country = "unknown";
		}
		System.out.println(n + " -> " + country);
	}
}
```

Another kind of **switch** is the so called *switch expression.*
This is an *expression,* which means that the switch as the whole has a value. Therefore, each arm of the **switch** expression must itself be an expression, i.e. have a value (of the same type, or at least the types must be convertible to one common type).
It can be just an expression, or a block ending with a **yield value** - then the value indicated after the **yield** statement will be the value of the corresponding arm.
As the switch expression must have a value, it has to be **exhaustive**, i.e. for all possible values there must be a matching switch label. For integral types and **String**s the number of possible values is practically infinite, so there is no way to avoid the **default** arm, as in the example below:
```java title:SwitchExpr.java
public class SwitchExpr {
	public static void main (String[] args) {
		int i = 7;
		var res = switch(i) {
			case 1, 2, 3 -> "First quarter";
			case 4, 5, 6 -> "Second quarter";
			case 7, 8, 9 -> {
				System.out.println("And here a block");
				System.out.println("still we need a value");
				yield "Third quarter";
			}
			case 10, 11, 12 -> "Fourth quarter";
			// must be exhaustive
			default -> "Something went wrong";
		};
		System.out.println("res = " + res);
	}
}
```

## Arrays
Arrays are the simplest data structure. An array can be viewed as a fixed-size collection of elements of the same type, in which elements are ordered and can be accessed by specifying their index.
Indices start with 0 (first element), so the last element has index **size-1**, where **size** is the size (length, dimension) of the array, i.e., number of its elements.
In Java, arrays are *objects* - this means that they carry not only information on their elements, but also some other information, in particular on their size. It also means that they are always created on the heap and never have names: we can refer to them using only *references* to them

#### Creating arrays
Arrays can be created in several way, illustrated in the example below. Points to note:
+ When an array is created, its size must be specified, and then cannot be modified.
+ The type *reference to array of elements of type* **Type** is denoted by **Type[].** Statement `{java} int[] arr;` means that **arr** is a reference to an array of **int**s - only a reference (with a value of **null**) is created,
+ If **arr** is  a reference to an array, the expression **arr.length** if of type **int** and its value is the length (size, dimension) of the array referenced to by **arr**.
+ Individual elements of an array can be accessed by their indices - if **arr** is the reference to an array, the expression `{java} arr[i]` denotes its **i**th element; remember, however, that **indexing starts from zero** 
+ There is a special kind of loop which can be used to iterate over elements of any array (and, as we will see later, over elements of other types of collections as well). It's sometimes called a "for-each loop" and has the form `{java} for (Type elem : arr) { ... }` where **Type** is the type of elements of the array **arr**, **elem** is any identified, and **arr** is the reference to an array. In consecutive iterations of the loop, **elem** will be a *copy* of the consecutive element of the array.
For example, this is how we can create a 10-element array of **char**s and fill it with random capital Latin letters (note the keyword **new**). Then we print its elements, separated by spaces, in one line:
```java
char[] arr = new char[10];
for (int i = 0; i < arr.length; ++i) {
	arr[i] = (char)('A' + (int)(Math.random()*26));
}
for (char c : arr)
	System.out.print(c + " ");
System.out.println();
```
