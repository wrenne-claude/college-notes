## SQL
SQL, or the Structured Query Language is a standardized language used to manage and manipulate data within relational databases. It allows users to create, read, update and delete data, as well as manage database structures, making it central to working with relational databases.
#### How was it created?
SQL was developed in the 1970s at IBM by researchers Donald D. Chamberlin and Raymond F. Boyce. They designed it as a way to interact with their experimental relational database system called [[Semester 1/WSI/Lecture 1#^d42249|System R]]. SQL became a powerful tool as it allowed users to work with data in a way that resembled natural language

**Standardization and Popularity**
Recognizing its potential, ANSI adopted SQL as a standard in 1986, followed by ISO in 1987. Over time, SQL has become the standard language for querying relational databases, supported by many systems such as MySQL, PostgreSQL, SQL Server, and Oracle, each with minor variations.

## SQL dialects
Different **dialects** of SQL exist because various DBMS have developed their own versions of SQL with unique features and syntax variations. While all SQL dialects share the core SQL standard - commands like `SELECT`, `INSERT`, `UPDATE` and `DELETE` - each DBMS may add or modify certain functionalities to better support their specific features and optimizations.

For example:
+ [[Semester 1/WSI/Lecture 2#^11ec2b|MySQL]] has a dialect with unique functions for handling data types and provides specific storage engine options
+ [[Semester 1/WSI/Lecture 2#^c98a94|PostgreSQL]] offers advanced features like JSONB (for JSON data), and extensive support for complex data types and window functions
+ [[Semester 1/WSI/Lecture 2#^7bcd1e|Microsoft SQL Server]] (T-SQL) adds procedural extensions, such as support for local variables, error handling, and specific transaction controls.
+ **Oracle SQL** has proprietary features like hierarchical queries, specialized functions, and PL/SQL, a procedural extension for writing complex logic.

**Why do we have these dialects?**
SQL dialects evolved to meet the specific needs and optimizations of each DBMS, allowing for improved performance, extended functionality, and unique tools tailored to different use cases. This diversity gives developers more options when choosing a database system that best aligns with their application's requirements.

## Imperative vs Declarative languages
#### Imperative:
Java, C#, C++, Python, etc. are all imperative languages, which means that whenever we have a program, we have a state and behavior.
When programming we declare and initialize some variables and use that data later on in the code. We have the memory (**state**) and the actions (**behavior**).

Imperative programming can be compared to a cookbook recipe. It gives you a list of ingredients (**data**), step-by-step instructions (**code**), all for you to cook a dish (**the program/outcome**). This analogy is good, because cookbooks can and do contain loops, conditionals, and variable assignments.
#### Declarative:
SQL, Puppet, Chef, HTML are all declarative languages, which means that we feed them commands on what to achieve, without explicitly stating *how* to achieve things.

We define our desired result and the system figures out the steps to achieve that result.
