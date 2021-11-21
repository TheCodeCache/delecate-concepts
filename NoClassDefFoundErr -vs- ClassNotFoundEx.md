`ClassNotFoundException` and `NoClassDefFoundError` occur when a particular class is not found at runtime.  
  However, they occur at different scenarios.  

# ClassNotFoundException

- It is a `runtime exception` thrown by an `application` when it tries to load a class at runtime  
  using the `Class.forName()` or `loadClass()` or `findSystemClass()` methods,  
  and the class with specified name are not found in the `classpath`  
- It occurs when `classpath is not updated with required JAR files`.

A basic typical example: `java.lang.ClassNotFoundException: oracle.jdbc.driver.OracleDriver`

```java
public class Main {
  public static void main(String[] args) {
    try {
      Class.forName("oracle.jdbc.driver.OracleDriver");
    } catch (ClassNotFoundException ex) {
      ex.printStackTrace();
    }
  }
}
```  

It throws below exception trace:  

```java
java.lang.ClassNotFoundException: oracle.jdbc.driver.OracleDriver
at java.net.URLClassLoader.findClass(Unknown Source)
at java.lang.ClassLoader.loadClass(Unknown Source)
at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
at java.lang.ClassLoader.loadClass(Unknown Source)
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Unknown Source)
at com.Main.main(MainClass.java:17)
```  

# NoClassDefFoundError 

- It is an `error` that is thrown when the `Java Runtime System` tries to load the definition of a class,  
  and that class definition is no longer available.  
  The required class definition was present at compile time, but it was missing at runtime  
- It occurs when required class definition is missing at runtime.

A basic typical example: `Exception in thread "main" java.lang.NoClassDefFoundError: com/example/samples/array/A`  

```java
class A {
  // some code
}

public class B {
  public static void main(String[] args) {
    A a = new A();
  }
}
```
When we `compile` the above program, two `.class` files will be generated. One is `A.class` and another one is `B.class`.  
  If we `remove` the `A.class` file and run the `B.class` file, `Java Runtime System` will throw `NoClassDefFoundError` like below:  

```
Exception in thread "main" java.lang.NoClassDefFoundError: A
at MainClass.main(MainClass.java:10)
Caused by: java.lang.ClassNotFoundException: A
at java.net.URLClassLoader.findClass(URLClassLoader.java:381)
at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:331)
at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
```

# An Important NOTE:  

What if, instead of `removing` an existing .class file, we `replace` it with a totally different .class file  
  but with same class name, off-course, with the same package.  
So, It will still work using the latest .class file w/o any problem, and in fact this is how it works in reality,   
  and should work ideally, otherwise we'd not be able to apply `patches` or `updates` or `upgrades` in production environments   
For ex:  
  in the previous code snippet example,  
  if we `separately compile` the below definition of class A and replace the existing `A.class` in the `classpath`:  

```java
import java.io.Serializable;

public class A implements Serializable {
  /**
   * 
   */
  private static final long serialVersionUID = 3989797797L;
  private String msg = "hello";
  // some code

  public String getMsg() {
    return msg;
  }

  public void setMsg(String msg) {
    this.msg = msg;
  }

  @Override
  public String toString() {
    return this.msg;
  }
}
```

**Reference:**  
1. https://dzone.com/articles/java-classnotfoundexception-vs-noclassdeffounderro

