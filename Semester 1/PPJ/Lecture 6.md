## Arrays
This is how we can create an array and initialize it at the same time; note that we don't specify its size, because the compiler will be able to infer it from the initializer in braces; after creation, we print it in reverse order:
```java
int[] arr = {1, 2, 8, 9};
for (int i = arr.length - 1; i >= 0; --i)
	System.out.print(arr[i] + " ");
System.out.println();
```

This next example shows another way to create and initialize an array:
```java
int[] a0 = new int[]{1, 2, 3};
int[] a1 = {4, 5, 6};
int[] arrsum = new int[a0.length]; // contains zeros
for (int i = 0; i < arrsum.length; ++i)
	arrsum[i] = a0[i] + a1[i];
for (int n : arrsum)
	System.out.print(n + " ");
```

The example below shows how to find the value of the maximum element of an array:
```java
int[] arr = {1, -6, 9, -2, 7};
int mx = arr[0];
for (int i = 1; i < arr.length; ++i)
	if (arr[i] > mx) mx = arr[i];
System.out.println("Maximum element is " + mx);
```

Sometimes what we want is rather the index of the maximum element:
```java
int[] arr = {1, -6, 9, -2, 7};
int indmax = 0;
for (int i = 1; i < arr.length; ++i)
	if (arr[i] > arr[indmax]) indmax = i;
System.out.println("Maximum element has index " + indmax);
```

How to reverse the order of elements in an array **arr** of **int**s:
```java
for (int i = 0, j = arr.length-1; i < j; ++i, --j) {
	int tmp = arr[i];
	arr[i] = arr[j]
	arr[j] = tmp;
}
```
Note that the condition `{java} i<j` cannot be replaced by `{java} i<arr.length` - we would then reverse the order of elements twice, thus restoring the original order!

And how can we randomly shuffle the elements of an array?
```java
int[] arr = {1, 2, 3, 4, 5, 6};
for (int i = 0; i < arr.length-1; ++i){
	int r = i + (int)((arr.length-i)*Math.random());
	int tmp = arr[i];
	arr[i] = arr[r];
	arr[r] = tmp;
}
```

#### Arrays of references to objects
Arrays of objects do not exist in Java (as they *do* exist in C++). Instead we can create arrays of references (pointers) to objects. If not initialized otherwise, all elements of such an array will initially be **null:**
```java
public class ArrStrings{
	public static void main (String[] args) {
		String[] arr = null;
		System.out.println(arr);
		
		arr = new String[4];
		// prints: null null null null
		for (String s : arr) System.out.print(s + " ");
		System.out.println();
		
		arr[0] = arr[2] = "Ala"
		// prints: Ala null Ala null
		for (String s : arr) System.out.print(s + " ");
		System.out.println();
	}
}
```

#### Multi-dimensional arrays
Strictly speaking, there are no multi-dimensional arrays in Java. However, it is possible that elements of an array are references to arrays of some type. Therefore, after
```java
int[][] b = { {1, 2, 3}, {4, 5, 6, 7}, {11, 12} };
```
the variable **b** is the reference to an array of references to arrays of ints. In particular, the type of `{java} b[1]` is *reference to array of ints,* in this case the array `{java} {4, 5, 6, 7}`. Expression `{java} b.length` is 3, as there are three references to arrays in **b,** while `{java} b[1].length` is 4, as `{java} b[1]` is the reference to an array of ints with four elements. The type `{java}int[][]` is *reference to array of references to arrays of **int**s.*

Note also, that all elements of a "two-dimensional" array are references to "normal" arrays of the same type, but not necessarily of the same length (as shown above). Such arrays, where rows are of different lengths, are called **jagged arrays** (or "ragged" arrays). However, very often they *do* have the same length - we call such 2D arrays **rectangular arrays,** as we can visualize them as rectangles of elements (called *matrices* in mathematics):
```java
int[][] arr = { {  1,  2,  3,  4},
			    { 11, 22, 33, 44},
			    { -1, -2, -3, -4} };
```
Individual arrays are called **rows** of this array - they correspond to `{java} arr[0], arr[1], arr[2]`. Elements with the same *second* index are called **columns:** in the above example elements `{java}arr[i][1]` where $i=0, 1, 2$, are the second (with index 1) column of the array (numbers 2, 22, -2)

In particular, the number of columns in a rectangular array may be equal to the number of rows - it is then a **square array.** For example, the following array is a square array 4x4:
```java
int[][] squ = { {  1,  2,  3,  4},
			    {  5,  6,  7,  8},
			    {  9, 10, 11, 12},
			    { 13, 14, 15, 16} };
```
For square arrays it makes sense to talk about their diagonals.
The **main diagonal** (or just 'diagonal') consists of the elements for which the row and columns indices are the same, or in other words these are elements on the diagonal going from the upper-left corner to the lower-right one. The **antidiagonal** are elements for which the sum of row and column indices is fixed and equal to size-1, where **size** is the number of columns (equal to the number of rows). In other words, these are elements on the diagonal going from the upper-right corner to the lower-left one.

---
## Static functions
Classes usually contain, besides fields, constructors and methods (that we will cover later, when talking about classes) and **static functions** (or static methods). We can think about a function as a piece of code that can be executed (invoked) many times from other functions (for example, from **main**) in such a way that in each invocation some data that the function operates on may be different.
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