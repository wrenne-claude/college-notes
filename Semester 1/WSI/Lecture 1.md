Lecturer: Piotr Gago pgago@pjwstk.edu.pl


### Database
+ A **database** is an organized collection of data that allows you to store, manage and retrieve information efficiently. Think of it as a digital filing cabinet where different pieces of data (e.g. customer details, sales records) are stored in a structured way, making it easy to find and use them when needed.
+ **Data** refers to raw, unprocessed facts and figures without any context. It can be numbers, text, dates, or any other basic details collected during business operations. For example, individual sales transactions, customer names, or product prices are all data. On its own, data doesn't have much meaning, but when organized and analyzed, it becomes useful information.
+ **Information** is what you get when you process data to make it meaningful. For example, a database might store raw sales figures, but when you analyze this data to understand which product sells best during a certain period, you gain valuable information that helps in decision-making

### History of databases
The history of databases began in the 1960s when early computer systems needed a way to store and manage data more efficiently. Initially, data was stored in **flat files**, which were simple text files with no structure or relationships between data elements. This approach was cumbersome and inefficient, as finding and updating data was slow and prone to errors.

To address these challenges, the **hierarchical database model** emerged in the late 1960s, where data was organized in a tree-like structure with parent-child relationships, similar to an organizational chart. An example of this was IBM's *Information Management System* (IMS). While it improved data organization, it was rigid and not well-suited for handling complex relationships.

In the 1970s, the **network database model** was introduced, allowing more flexible connections between data elements. This model, known as the CODASYL DBTG (Conference on Data System Languages Database Task Group) model, used a graph structure where records could have multiple relationships. Despite offering more flexibility than the hierarchical model, it was still complex to manage and required specialized knowledge.

---

### Edgar F. Codd
The significant breakthrough came in 1970 when **Edgar F. Codd**, a computer scientist at IBM, introduced the concept of the **relational database model**. Codd's revolutionary idea was to organize data into tables (relations) with rows and columns, where each table represented an entity, and data could be linked through common attributes (keys). This model allowed for more flexibility, easier data manipulation, and a more intuitive way of representing complex relationships, leading to the development of the **Structured Query Language** (SQL) for interacting with the data. This concept laid the foundation for modern relational databases.

---

### First relational databases
The first database to implement Codd's relational model and some of his rules appeared in the 1970s and early 1980s. Here are a few of the pioneering relational database systems:
1. **IBM System R (1974-1977)**: Developed by IBM, system R was the first experimental database to implement Codd's relational model concepts. It introduced the use of SQL, which became the standard language for relational databases. While not a full commercial product, System R demonstrated the feasibility and advantages of relational databases, influencing future systems. ^d42249
2. **Ingres (1970s)**: Developed at the University of California, Berkeley, Ingres was one of the earliest relational database management systems to emerge after System R. It implemented many of Codd's ideas and used a query language called QUEL. Ingres eventually evolved into a commercial product and inspired other database systems, such as PostgreSQL.
3. **Oracle (1979)**: Oracle became the first commercially available RDBMS. Oracle's early versions were based on Codd's principles, using SQL as the query language. It was the first to implement a multi-platform RDBMS and gained popularity quickly, eventually becoming a dominant player in the database market.
4. **dBASE II (1980)**: Although not fully compliant with all of Codd's rules, dBASE II was one of the first successful commercial RDBMS for microcomputers. It played a significant role in popularizing relational databases among smaller businesses and individual users.

Other popular choices nowadays:
+ **PostgreSQL**: An open-source, advanced RDBMS known for its robustness, flexibility and support for complex queries. It adheres closely to SQL standards and offers many features like full ACID compliance, support for JSON data and extensibility through custom functions and data types. It's widely used in industries requiring reliability and data integrity.
+ **MySQL**: Another popular open-source RDBMS, MySQL is known for its speed, simplicity, and ease of use. It's widely used for web applications, including major platforms like WordPress. MySQL has a large community, making it a go-to choice for startups and small-to-medium-sized applications. It's less feature-rich compared to PostgreSQL but is well-suited for many common use cases.
+ **MariaDB**: A fork of MySQL created by its original developers after concerns about its acquisition by Oracle. MariaDB aims to remain fully open-source and provides additional features and optimizations over MySQL. It offers better performance in certain scenarios and maintains compatibility with MySQL, making it easy to switch between the two.

### Other kinds of databases
**NoSQL** databases are a type of database designed to handle unstructured, semi-structured, or rapidly changing data that doesn't fit well into the rigid structure of relational databases. Unlike relational databases, which use tables and SQL, NoSQL databases offer more flexibility by allowing different data models such as key-value, document, column-family, and graph.
+ **Key-Value Stores** (e.g. Redis, DynamoDB): Data is stored as a simple pair of keys and values, similar to a dictionary. This model is ideal for applications needing fast, simple data retrieval, such as caching.
+ **Document Stores** (e.g. MongoDB, Couchbase): Data is stored in documents (often JSON or BSON), allowing nested structures and varying data formats. This makes it suitable for handling complex, evolving data, like user profiles or product catalogs.
+ **Column-Family Stores** (e.g. Cassandra, HBase): Data is stored in columns rather than rows, which makes it efficient for querying large datasets with similar attributes. It's often used for handling big data and real-time analytics.
+ **Graph Databases** (e.g. Neo4j, Amazon Neptune): Data is represented as nodes and edges, making it ideal for applications that need to model and analyze relationships, such as social networks or recommendation engines.