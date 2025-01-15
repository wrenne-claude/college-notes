## Constructors and methods

Let us make the fields of a class **private.** For example:
```java
public class VerySimple {
	private int age;
	private String name;

	// constructor
	public VerySimple(int age, String n) {
		this.age = age;
		name = n;
	}

	// getter
	public int getAge() {
		return age;
	}

	// setter
	void setAge(int a) {
		age = a;
	}

	// getter (with no corresponding setter)
	public String getName() {
		return name;
	}
}
```
and in **Main** we can create objects of this class, and even modify them (because both constructor and **setAge** are not **private** or **protected.** Of course, in our **main** function, which is a function of another class, we cannot directly access the fields of class **VerySimple,** but we can use public constructors and methods, which, being members of the class **VerySimple,** *do* have access to all members of *all* objects of this class. In particular, **constructor** is a very special function:
+ its name must be the same as the name of the class;
+ it does not declare any return type (even **void**);
+ it will be automatically invoked *only* at the very end of the process of constructing an object - there is no way to invoke it on an object which has already been created before.
Normally, constructor are used to initialize fields of the object being created, but generally they can do whatever we wish.
```java
public class Main {
	public static void main(String[] args) {
		VerySimple alice = new VerySimple(23,"Alice");
		VerySimple bob = new VerySimple(21,"Bob");
		alice.setAge(18);
		System.out.println(alice.getName() + " " + alice.getAge())
		System.out.println(bob.getName() + " " + bob.getAge())
	}
}
```

To use a specific constructor during creation of an object, we just write, after the name of the class, arguments - as many of them as expected by the constructor, and of appropriate types.

## Static members
Any class can also declare **static** members - both fields (data) and methods (but *not* static constructors!). We can imagine a static members as belonging the class as a whole, not to objects. As such, they can be used even if we haven't created any objects of our class - they are brought into existence and initialized when the class is loaded by the JVM (if the class happens to be an enum, *after* all the enum values have been created).
Inside a static function there is no **this,** which normally exists and is the reference to the object the function was invoked on - static functions are *not* involved on any object and consequently cannot use **this.** From the outside of a class, we refer to its static members using just the name of the class. We *can,* although it's very confusing, use reference to *any* object of this class for the same purpose.
For example, in the last line of
```java
public class AnyClass {
	public static int stat;
	// ...
}

// somewhere else

AnyClass.stat = 7;
AnyClass a = new AnyClass();
// ...
a.stat = 28;
```
we refer to static member **stat** just by putting **a** before the dot, but the compiler will use only the information about the type of **a** - which particular object of class **AnyClass** is used in this context is completely irrelevant. Looking at this line alone, one is not able to tell whether **stat** is a static of non-static member of the class; for this reason it is recommended to always use the first syntax, with the name of a class, as here, it is obvious that **stat** must be static.

In the following example:
```java
public class StatExample {
	private static double rate = 1;
	private static char ID = 'A';

	private double amount;
	private char id;

	public static void setRate(double r) { rate = r; }
	public static double getRate() { return rate; }

	StatExample(double a) {
		id = ID++;
		amount = a;
	}

	@Override
	public String toString() {
		return "I'm " + id + ". I have $" + amount + 
				" = " + rate*amount + " PLN";
	}

	public static void main (String[] args) {
		StatExample.setRate(4.1);
		StatExample sa = new StatExample(10);
		StatExample sb = new StatExample(16);
		StatExample sc = new StatExample(20);
		System.out.println(sc + "\n" + sb + "\n" + sa);
	}
}
```
The program prints:
`I'm C, I have $20.0 = 82.0 PLN`
`I'm B, I have $16.0 = 65.6 PLN`
`I'm A, I have $10.0 = 41.0 PLN`

Both methods and static functions can be recursive, that is, they can invoke themselves; of course, you have to ensure that the chain of recursive invocations stops at some point...
```java
public class SimpleRec {

	// should be called with from=0
	static void printArrRec(int[] arr, int from) {
		if (from == arr.length) {
			System.out.println();
			return;
		}
		System.out.print(arr[from] + " ");
		printArrRec(arr,from+1);
	}

	// should be called with from=0
	static void printArrRecReverse(int[] arr, int from) {
		if (from == arr.length) return;
		// first invoke next then print
		printArrRecReverse(arr,from+1);
		System.out.print(arr[from] + " ");

		if (from == 0) System.out.println();
	}

	// should be called with from=0, to=arr.length
	static void revArrayRec(int[] arr, int from, int to) {
		if (to-from <= 1) return;
		int temp = arr[from];
		arr[from] = arr[to-1];
		arr[to-1] = temp;
		revArrayRec(arr,from+1,to-1);
	}

	// should be called with from=0
	static int maxElemRec(int[] arr, int from) {
		if (from == arr.length-1) return arr[arr.length-1];
		return Math.max(arr[from],maxElemRec(arr,from+1));
	}

	// should be called with from=0
	static void selSortRec(int[] arr, int from) {
		if (from == arr.length-1) return;
		int indmin = from;
		for (int i = from+1; i < arr.length; ++i)
			if (arr[i] < arr[indmin]) indmin = i;
		int temp = arr[from];
		arr[from] = arr[indmin];
		arr[indmin] = temp;
		selSortRec(arr.from+1);
	}

	static int gcd(int a, int b) {
		return b == 0 ? a : gcd(b, a%b);
	}

	static int fact(int n) {
		return n <= 1 ? 1 : n*fact(n-1);
	}

	// must be called with k=2
	static boolean isPrime(int n, int k) {
		if (k*k > n) return true;
		if (n%k == 0) return false;
		return isPrime(n,k+1);
	}

	static long counter = 0;
	// stupid way of calculating Fibonacci numbers
	static long fibo(int n) {
		++counter;
		return n <= 1 ? (long)n : fibo(n-2) + fibo(n-1);
	}

	public static void main(String[] args) {
		// Arrays
		int[] a = {13,3,55,7,9,11};
		printArrRec(a,0);
		revArrayRec(a,0,a.length);
		printArrRec(a,0);
		selSortRec(a,0);
		printArrRec(a,0);
		printArrRecReverse(a,0);
		System.out.println("Max. in a: "+maxElemRec(a,0));

		// Greatest Common Divisor
		System.out.println(gcd(5593,11067));

		// Factorials
		System.out.println("10! = " + fact(10));
		System.out.println("12! = " + fact(12));

		// Primes
		System.out.println("Primes up to 100");
		for (int n = 2; n <= 100; ++n)
			if (isPrime(n,2)) System.out.print(n+" ");
		System.out.println();

		// Fibonacci numbers
		for (int n = 40; n <= 46; n += 2) {
			counter = 0;
			long r = fibo(n);
			System.out.println("Fibo(" + n + ") = " + r + "; counter = " + counter);
		}
	}
}
```

The program prints
`13 3 55 7 9 11`
`11 9 7 55 3 13`
`3 7 9 11 13 55`
`55 13 11 9 7 3`
`Max. in a: 55`
`119`
`10! = 3628800`
`12! = 479001600`
`Primes up to 100`
`2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 71 73 79 83 89 97`
`Fibo(40) = 102334155; counter = 331160281`
`Fibo(42) = 267914296; counter = 866988873`
`Fibo(44) = 701408733; counter = 2269806339`
`Fibo(46) = 1836311903; counter = 5942430145`

## Initializing blocks

## Singleton classes
Very often we encounter the situation when we have a class of which at most one object should ever be created; such objects are called singletons. There are at least two approaches to produce such objects. If the object in question is expensive to create and it is possible that it will not be needed at all, we can use lazy evaluation approach:
```java title:Connect.java
public class Connect {
	private static Connect connection = null;

	private Connect()
	{ } // private - no one can create any other object

	public static connect getInstance() {
		// lazy evaluation, no multithreading
		if(connection == null) {
			connection = new Connect();
		}
		return connection;
	}
}
```
Of, if we know that such an object almost surely will be required, one can use eager evaluation:
```java title:Config.java
public class Config {
	// eager evaluation
	private final static Config config = new Config();

	private Config() {
		// ...
	}

	public static Config getInstance() {
		return config;
	}
}
```
The program convinces us that there if only *one* object of each of the classes. Note, however, that this will be a lot more complicated in the face of multithreading!
```java title:Main.java
public class Main {
	public static void main(String[] args) {
		Connect con1 = Connect.getInstance();
		Connect con2 = Connect.getInstance();
		if (con1 == con2) System.out.println("con1==con2");
		Config cnf1 = Config.getInstance();
		Config cnf2 = Config.getInstance();
		if (cnf1 == cnf2) System.out.println("cnf1==cnf2");
	}
}
```