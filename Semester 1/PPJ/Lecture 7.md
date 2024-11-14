Sometimes we would like to add an element to an array. This is impossible, as the lengths of arrays are fixed and cannot be changed after creation. However, there are ways to do so under some restrictions.
We can insert a new element somewhere at a given position just by shifting all elements to the right of the one to be inserted by one position to make room for it:
```java title:ShiftArray.java
import java.util.Arrays;

public class ShiftArray {
	public static void main(String[] args) {
		// 'Inserting' a value
		int[] a = {4, 5, -2, 4, 1, 6, 7};
		int ind = 3;
		int value = 9;
		System.out.println("'Inserting' a value " + value +
						   " at index " + ind);
		System.out.println(Arrays.toString(a));
		for (int i = a.length-1; i>ind; --i) //must be backwards
			a[i] = a[i-1];
		a[ind] = value;
		System.out.println(Arrays.toString(a));
	}
}
```

```java title:ExpandArray.java
import java.util.Arrays;

public class ExpandArray {
	public static void main(String[] args) {
		//'Expanding' by inserting a value
		// at a given index
		int[] a = {4, 5, -2, 4, 1, 6, 7};
		int ind = 3;
		int value = 9;
		System.out.println(Arrays.toString(a));
		int[] b = new int[a.length+1]; // longer array
		for (int i = 0; i<ind; ++i)
			b[i] = a[i];
		for (int i = ind+1; i<b.length; ++i)
			b[i] = a[i-1];
		b[ind] = value;
		System.out.println(Arrays.toString(b));
	}
}
```

```java title:RemoveElem.java
import java.util.Arrays;

public class RemoveElem {
	public static void main(String[] args) {
		//'Removing' the element with a given index
		int[] a = {1, 2, 4, 7, 4, 2, 8};
		int ind = 3;
		System.out.println("'Removing' element with index " + ind);
		System.out.println(Arrays.toString(a));
		for (int i = ind; i < a.length-1; ++i)
			a[i] = a[i+1];
		System.out.println(Arrays.toString(a));
	}
}
```

```java title:ShrinkArray.java
import java.util.Arrays;

public class ShrinkArray {
	public static void main(String[] args) {
		//'Removing' the element with a given index
		// and 'shrinking' the array
		int[] a = {1, 2, 4, 7, 4, 2, 8};
		int ind = 3;
		System.out.println(Arrays.toString(a));
		int[] b = new int[a.length-1];
		for (int i = 0; i<ind; ++i)
			b[i] = a[i];
		for (int i = ind; i<b.length; ++i)
			b[i] = a[i+1];
		System.out.println(Arrays.toString(b));
	}
}
```

```java title:SplitArray.java
import java.util.Arrays;

public class SplitArray {
	public static void main(String[] args) {
		//'Splitting' an array into two arrays
		// and/or one two-dimensional array
		int[] a = {4, 5, -2, 0, 4, -1, 6, 0, -7, 9};
		int numNeg = 0;
		int numPos = 0;
		for (int i = 0; i<a.length; ++i)
			if      (a[i] < 0) ++numNeg;
			else if (a[i] > 0) ++numPos;
		int[] aneg = new int[numNeg];
		int[] apos = new int[numPos];
		
		for (int i = 0, ineg = 0, ipos = 0; i<a.length; ++i)
			if      (a[i] < 0) aneg[ineg++] = a[i];
			else if (a[i] > 0) apos[ipos++] = a[i];
		System.out.println(Arrays.toString(a));
		System.out.println(Arrays.toString(aneg));
		System.out.println(Arrays.toString(apos));
		
		// Array of arrays (two-dimensional array)
		int[][] aa = {aneg, apos};
		// or int[][] aa = new int[][]{aneg, apos};
		// or int[][] aa = new int[2][];
		//     aa[0] = aneg;
		//     aa[1] = apos;
		System.out.println("\nBefore swapping");
		System.out.println(Arrays.toString(aa[0]));
		System.out.println(Arryas.toString(aa[1]));
		
		// Swapping rows
		int[] tmp = aa[0];
		aa[0] = aa[1];
		aa[1] = tmp;
		System.out.println("\nAfter swapping");
		System.out.println(Arrays.toString(aa[0]));
		System.out.println(Arrays.toString(aa[1]));
	}
}
```

## Functions
#### Non-recursive functions
The definition of a static function is of the form
```java
[access] static Type funName(Type1 parName1, Type2 parName2, ...) {
	// body of the function
}
```
and consists of
+ The keyword **static** (there are also functions which are *not* static). Before or after this keyword we could place an access specifier of the function (**public** or **private**)
+ The name of the type of a result which this function yields (the so-called *return type*); **void,** if the function doesn't return any result
+ A name of the function; it should always start with a lower-case letter but is otherwise arbitrary.
+ In round parentheses, a list of parameters: these are comma separated pairs **Type parName** where **Type** is the name of a type and **parName** is an arbitrary name of this parameter (it should start with a lower-case letter). The list of parameters can be empty, but parentheses are always required.
+ The body of the function enclosed in braces.
Names of parameters are arbitrary and have nothing to do with names declared in other functions (as their parameters or variables are defined inside them). We invoke (call) the function by its name with **arguments** corresponding to the function's parameters enclosed in round parentheses:
`{java icon} ... funName(arg1, arg2, ...) ...`
![[Pasted image 20241112125403.png]]

An example of a rather trivial function would be
```java
static double maxOf3(double a, double b, double c) {
	double mx = a;
	if (b > mx) mx = b;
	if (c > mx) mx = c;
	return mx;
}
```
and then, somewhere in **main** or another function:
```java
double u = 1, v = 2, w = 2;
// ...
double result = maxOf3(u, v+1, w-1);
```
As we can see, the arguments do not need to be variables - what matters are their values, copies of which will be put on the stack and will be available for the function under names a, b, and c (and will 'disappear' when the function exits).

It is very important to realize how the arguments are passed to the function. For example, suppose we have a function
```java
public static int fun(int a) {
	a = a + 99;
	return a;
}
```
Then, after (somewhere in another function)
```java
int a = 1;
int res = fun(a);
```
the value of res will be 100, but the value of **a** will still be 1, as only the copy of its value was accessible to the function; this copy was modified but it disappeared after the return anyway.
All this applies also to passing objects, for example arrays (which *are* objects).