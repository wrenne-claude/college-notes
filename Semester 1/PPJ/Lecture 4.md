### Exclusive OR - XOR (^)
If expr1 and expr2 have values of type **boolean**, then the expression
expr1 ^ expr2
is true only if expr1 and expr2 are different from each other

The **conditional expression** is the only *ternary* operator, that is an operator with three operands. It looks like this:
cond ? expr1 : expr2
Here **cond** is a **boolean**. If it is **true**, then the value of expr1 will become the value of the whole expression and expr2 will not be evaluated; if **cond** is false, then the value of expr2 becomes the value of the whole expression and expr1 will not be evaluated. The simplest example would be: (a and b are **ints**):
`{java icon} int mx = a > b ? a : b;`
which initializes mx with the bigger of a and b values. The ternary operator resembles the **if...else** if construct, but is *not* equivalent! In particular, the expression `b ? e1 : e2` has a value, while **if...else** if has not. For example,
`{java icon} a > b ? System.out.print("a") : System.out.print("b"); // NO!`
doesn't make sense, because **print** has no value.

### Casting operator
Some values can be, in a natural way, converted to values of a different type. If such conversion does not lead to a loss of info, it can be performed by the compiler automatically (*implicit conversion*), as in
`{java icon} int a = 7;`
`{java icon} double x = a;`
If the conversion is possible, but would lead to a loss of information, we have to enforce it explicitly:
`{java icon} double x = 7.5;`
`{java icon} int a = (int)x;`
Of course, not every conversion makes sense, for example:
`{java icon} double x = 7.5;`
`{java icon} String s = (String)x; //WRONG`
is impossible. Generally, conversions apply to numeric types; they also can be used for references.
Unlike in many other languages, there are no conversions between numeric (+reference) types and logical values.

### Precedence and associativity
Operators may have different precedence (priority). For example, in
`{java icon} d = a + b * c;`
b could be the right operand of addition or the left operand of multiplication, but we know that multiplication has higher priority, so it is equivalent to `{java icon} d = a + (b * c);`, rather than `{java icon} d = (a + b) * c;`.
Sometimes, however, it is not so obvious.
Is the statement `{java icon} if ( a << 2 < 3) System.out.println("yes");` correct or not?
If << has higher priority than <, then it is equivalent to
`{java icon} if ( (a<<2) < 3) System.out.println("yes");` which makes sense.
But if < is stronger, then `{java icon} if (a << (2<3)) System.out.println("yes"); //NO!!!`
would not make any sense. If in doubt, just add parentheses to make your intentions clear.

Another property of operators is **associativity:** it tells, whether in a series of operations with equal priority (without parentheses), they will be performed from left to right or from right to left. All binary operators are left-associative (from left to right) with the exception of assignment, which is right-associative; something like this:
`{java icon} int a, b = 1, c;`
`{java icon} c = a = b;`
is correct, because it is equivalent to
`{java icon} int a, b = 1, c;`
`{java icon} c = (a = b);`
while
`{java icon} int a, b = 1, c;`
`{java icon} (c = a) = b;`
would not compile, because we are assigning uninitialized value of **a** to **c**.
The ternary (conditional) operator is also right-associative; this instruction
`{java icon} String s = a == b ? "equal" : a > b ? "a" : "b";`
is correct, because it is equivalent to
`{java icon} String s = a == b ? "equal" : (a > b ? "a" : "b");`
while
`{java icon} String s = (a == b ? "equal" : a > b) ? "a" : "b"; //WRONG`
would be incorrect, as the expression to the left of the second **?** doesn't evaluate to a **boolean** value.

---
The table below illustrates precedences and associativity of Java operators.
--> denotes associativity from left to right,
<-- denotes associativity from right to left.
Operators are shown in decreasing order of their precedence.
![[Pasted image 20241022125703.png]]

---

### Conditional statements
Conditional statements may look like this:
```java
if (cond) {
	//...
}
//or
if (cond1) {
	//...code 1
} else if (cond2) {
	//...code 2
} else if (cond3) {
	//...code 3
} else {
	//...code 4
}
```
where **cond** are expressions whose values are of type **boolean**. The **else if** clauses are optional, as is the **else** clause; however, if they are used, the **else** clause must be the last.
Conditions are checked in order, and for the first which evaluates to **true**, the corresponding block of code will be executed (subsequent blocks will be ignored). If the **else** clause is present, the corresponding block will be executed if none of the previous conditions are **true.** If there is only one instruction in the block corresponding to a condition, the curly braces are not obligatory (although recommended).
In the following example, we check if a given year is a leap year or not:
```java title:LeapYear.java
import java.util.Scanner;
public class LeapYear{
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		System.out.print("Enter a year (int): ");
		int year = scan.nextInt();
		scan.close();
		boolean is_leap;
		
		if (year%400 == 0)
			is_leap = true;
		else if (year%100 == 0)
			is_leap = false;
		else if (year%4 == 0)
			is_leap == true;
		else
			is_leap == false;
		System.out.println("Year " + year + " is " + 
						   (is_leap? "" : "not ") + "a leap year");
	}
}
```

### Switch statement and expression
There are two kinds of **switch** instructions in Java. First, let us consider the "classic" form of this instruction: **switch statement**. It resembles a series of **else if** statements (but is not equivalent).
It looks like this:
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
		// should we break?
	// ...
	default:
		statement1;
		// ...
		statementN;
		break;
}
```
The value of **expr** (the so called *selector*) must be parenthesized and be of an integral type (but not **long**), or one of the corresponding boxed types (**Integer, Short,** etc.), or the reference to a **String,** or an enumeration constant. The symbols **val** stand for values with which the value of **expr** will be compared (in the specified order). They have to be literal values (not variables). If the value of **expr** is equal to any of the **vals**, the code in the corresponding arm is executed and then execution continues (*falls through*) with all the arms below. Normally, this is not what we want, so to avoid it, we use **break**, which transfers control flow out of the **switch** block (sometimes this "falling through" may just be what we want, as in the example below). At the end of this example, we used the **default** arm, where we don't make any comparisons: this will be the arm selected if all other comparisons yield **false.** The **default** clause is optional and doesn't have to appear as the last.

```java title:SimpleSwitch.java
import java.util.Scanner;

public class SimpleSwitch {
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		System.out.print("Enter an initial: ");
		char initial = scan.next().charAt(0);
		scan.close();
		
		switch (initial) {
			case 'A':
			case 'a':
				System.out.println("Amelia");
				break;
			case 'B':
			case 'b':
				System.out.println("Barbara");
				break;
			case 'C':
			case 'c':
				System.out.println("Cindy");
				break;
			case 'D':
			case 'd':
				System.out.println("Doris");
				break;
			default:
				System.out.println("Invalid input");
		}
	}
}
```

### Loops
#### While loop
The simplest form of a loop.
```java
while (condition) {
	// ...
	if (cond1) break; //optional
		// ...
	if (cond2) continue; //optional
		// ...
}
```
where **condition** is an expression yielding a **boolean** value. The loop is executed as follows:
1. **condition** is evaluated, and if it is **false**, the flow of control jumps out of the loop;
2. if **condition** evaluates to **true**, the body of the loop (everything inside the block) is executed and then the flow of control goes back to item 1.
Inside the loop, you can (but don't have to) use **break** and **continue** instructions. When **break** is executed, the flow of control goes out of the loop immediately. When **continue** is encountered, the current iteration of the loop is considered completed, and we go back to the next iteration (so the **condition** is checked again).
The following loop will print square roots of integers read from the keyboard, but only of positive ones; the loop ends when the user enters 0:
```java
Scanner scan = new Scanner(System.in);
while (true) {
	int n = scan.nextInt();
	if (n == 0) break;
	if (n < 0) {
		System.out.println("Negative");
		continue;
	}
	System.out.println("square root of " + n + 
			" is " + Math.sqrt((double)(n)));
}
```
Note that assignment is an expression - it has a value. Therefore, we could have rewritten the above snippet as
```java
Scanner scan = new Scanner(System.in);
int n;
while ((n = scan.nextInt()) != 0) {
	if (n < 0) {
		System.out.println("Negative");
		continue;
	}
	System.out.println("Square root of " + n + 
			" is " + Math.sqrt((double)(n)));
}
```

#### *do-while* loop
Loops of this type are similar to **while-loop**s, but checking a condition is performed *after* execution of the body of the loop.
```java
do {
	// ...
	if (cond1) break; //optional
		// ...
	if (cond2) continue; //optional
		// ...
} while (condition);
```
Therefore,
1. the body of the loop is executed;
2. the value of **condition** is evaluated; if it is **true**, the flow of control goes to item 1. If it is **false,** then the flow of control jumps out of the loop.

#### *for* loop
A *for* loop looks like this:
```java
for ( init ; condition ; incr ) {
	// ...
	// ...
}
```
where (below, by **expression** we mean anything that has a value)
+ *init:* one declaration (possibly of several variables of the same type), or zero or more comma-separated expressions;
+ *condition:* expression with a value of type **boolean**; if left empty - interpreted as **true;**
+ *incr:* zero or more comma-separated expressions.
Any (or even all) of the three parts may be empty, but exactly two semicolons are always required.
The execution of a *for* loop proceeds as follows:
1. the *init* part will be executed once only, before entering the loop. If it is a declaration of one or more variables of the same type, they will exist only within the body of the loop - they are not visible (in fact, they don't even exist) when the flow of control goes out of the loop.
2. the *condition* part will be evaluated next (if left empty, it will be assumed **true**). If it evaluates to **false**, the loop ends and the flow of control goes out of the loop. If it evaluates to **true** then the body of the loop is executed.
3. When execution of the body of the loop is completed, the *incr* part is executed, and then we go back to item 2 (evaluation of the *condition*).
For example, the following snippet calculates and prints the sum of all natural numbers from the range [1,1000]
```java
int sum = 0;
for (int i = 1; i <= 1000; ++i) {
	sum += i;
}
System.out.println("Sum is " + sum);
```
In the example above, the braces could have been omitted, because the body of the loop consists of only one statement:
```java
int sum = 0;
for (int i = 1; i <= 1000; ++i) sum += i;
System.out.println("Sum is " + sum);
```
Note that we cannot declare **sum** in the *init* part of the loop, because it would not exist after exiting the loop, so we would not be able to print its value.