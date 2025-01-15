### Try-catch blocks
How do we handle exceptions? We enclose a fragment of our code where an exception may, at least potentially, occur in a **try** block of the **try-catch** construct:
```java
try {
	// ...
} catch(ExcType1 ex) {
	// handling the exception of type ExcType1
} catch(ExcType2 ex) {
	// handling the exception of type ExcType2
}
// ...other catch blocks
```

It is possible for one **catch** block to handle two (or more) types of unrelated exceptions (they are unrelated if none of them is a subtype of the other). We just specify these types separating their names with a vertical bar; for example in
```java
	// ...
	catch (IOException | SQLException e) {
		// ...
		throw e; // rethrowing exception
	}
}
```
the **catch** will catch exceptions of type IOException and SQLException as well (and their subclasses).

### finally block
After all catch blocks, we can (but don't have to) use a **finally block**.
```java
try {
	// ...
} catch(ExcType1 e) {
	// ...
} catch(ExcType2 e) {
	// ...
} finally {
	// ...
}
```
The code in finally block will always be executed.

### Propagating exceptions
Sometimes we know that an exception can occur but we don't know how to handle it. Then we can declare the whole function as throwing this kind of exception (or even, comma separated, exceptions of two or more types)
```java
void fun( /* parameters */ ) throws ExcType1, ExcType2 {
	// here we do NOT handle exceptions
	// of types ExcType1, ExcType2
}
```
## Throwing exceptions
In some situations, we can throw exceptions by ourselves. Suppose we implement, in class **Person**, a method setting the person's age:
```java
void setAge(int age) {
	this.age = age;
}
```
We may decide that trying to set a negative age is a user's error. We can signal such invalid attempt by throwing an exception of some type. Java defines many types of exceptions in its standard library - in this particular case **IllegalArgumentException** would be probably most appropriate. We thus rewrite our method like this:
```java
void setAge(int age) {
	if (age < 0)
		throw new IllegalArgumentException("age<0");
	this.age = age;
}
```
This exception is unchecked, so we don't have to handle it or to declare the method as throwing it.

### Assertions
Another way of dealing with possible errors in our programs is by using *assertions.* After the keyword **assert,** we specify a condition (something with a boolean value) and, after a colon, a message (which is optional)
`{java icon} assert boolExp : message;`
