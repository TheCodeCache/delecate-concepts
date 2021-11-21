
There is a thin line that separates a `method` and a `function`.  

A `method` is almost always used in the context of `Object-Oriented` concepts.  
A `method` always contains an implecit reference of its asociated object called `this`.  

However, a `function` can exist as a standalone entity. we can usually find them in procedural languages such as `C`  

A `method` can be of following 2 types:  
1. `static` method
2. `instance` method

**Method:**  
```java
class Template{

  // member varables/ attributes
  private String name;

  public static void staticMethod(){
    System.out.println("This is a static method");
  }

  // this definition is also called as `member` functions
  public void instanceMethod(){
    System.out.println("This is an instance method");
    // access the current object like this
    this.name; // implicitly referring to the current instance of the Class
  }
  
  public static void main(String[] args){
    Template.staticMethod(); // static method invocation
    
    Template template = new Template(); // object instantiation
    template.instanceMethod(); // instance method invocation
  }
}
```
**Function:**  
```C
#include stdio.h
#include conio.h

// The sample `function` definition in language `C`
void function(){
  printf("This is a smple function");
}

void main(){
  function(); // function invocation
  getch();
}
```

Thus, a `function` can be invoked directly as it is,  
  however, to invoke a `method` we must need either an object or the enclosing Class type.  


