# Study for Java

* Clean Code (2008), by Robert C. Martin
* Effective Java (2017), third edition, by Joshua Bloch
* pick 100 easy problems from [leetcode](https://leetcode.com/), try to solve them on your own, and compare your solution to the best one.
trails from the [official Java tutorials](https://docs.oracle.com/javase/tutorial/)
* [Custom Networking](https://docs.oracle.com/javase/tutorial/networking/index.html),
* [Generics](https://docs.oracle.com/javase/tutorial/extra/generics/index.html),
* [JavaBeans](https://docs.oracle.com/javase/tutorial/javabeans/index.html),
* [JDBC Database Access](https://docs.oracle.com/javase/tutorial/jdbc/index.html),
* [JMX](https://docs.oracle.com/javase/tutorial/jmx/index.html),
* [JAXB](https://docs.oracle.com/javase/tutorial/jaxb/index.html),
* [Reflection](https://docs.oracle.com/javase/tutorial/reflect/index.html), and
* [Security](https://docs.oracle.com/javase/tutorial/security/index.html) (a more interesting place for Java Security is actually here, which is referenced in this trail).
* [JDK Tools and Utilities](https://docs.oracle.com/javase/8/docs/technotes/tools/index.html#troubleshoot). In particular, pay special attention to the Troubleshooting Tools section!
* Gradle User Guide (eg, v2.5 docs)
  * [Plugin Development Tutorials](https://gradle.org/guides/?q=Plugin%20Development)
* [The official Jetty doc](https://www.eclipse.org/jetty/documentation/9.4.15.v20190215/)  For side projects
* Hadoop
  * Hadoop: The Definitive Guide (2015), by Tom White.
  * the official Apache Hadoop docs.
* [official Java EE tutorial](https://docs.oracle.com/javaee/7/tutorial/)
  * Part III Chapter 6 Getting Started with Web Applications
  * Part III Chapter 17 Java Servlet Technology
  * Part IV Bean Validation
  * Part V Contexts and Dependency Injection for Java EE
  * Part VI Web Services
  * Part VIII Persistence.
  * Part X Security.
* [Spring framework documentation](https://docs.spring.io/spring/docs/current/spring-framework-reference/index.html)
* Zookeeper
  * Chapter 21 Zookeeper, in Hadoop: The Definitive Guide (2015), by Tom White
  * [The official Apache Zookeeper documentation](https://zookeeper.apache.org/doc/r3.4.13/)

Four famous functional interfaces:

```JAVA
1. Supplier<T> =====> T get() ------> Factories in streams
2. Predicate<T> =====> boolean test(T) ------> filters in streams
3. Function<T, R> =====> R apply(T) -------> map in streams
4. Consumer<T> ======> void accept(T) -------> forEach in streams
```

MORE INFO ON LOOM
JEP Café - Virtual Threads:
<https://www.youtube.com/watch?v=IKSSBvRDmTg>
JEP Café - Launching 10 Million Concurrent Threads with Loom:
<https://www.youtube.com/watch?v=UVoGE0GZZPI>
JEP Café - Java Asynchronous Programming Full Tutorial with Loom and Structured Concurrency:
<https://www.youtube.com/watch?v=2nOj8MKHvmw>
