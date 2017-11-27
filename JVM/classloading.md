# Java Class Loading

Java class loading explanation



## What is Java Class Loading ?

Java class loader loads java classes into JVM dynamically (i.e during runtime ) , Java class loading corresponds to taking the
.class file from the secondary storage and store its binary data inside JVM method area .without the  concept of a ClassLoader,
it would not be possible to dynamically load new code into the JVM at runtime

The Java virtual machine has a component called class loader subsystem that is mainly  responsible for loading process 

![alt text](https://1.bp.blogspot.com/-tLOt9nQ-0ew/V5rt9-0LzRI/AAAAAAAACjs/F8dY9wUEBeAFVlEoXiNRsKLA4nKtjYXRQCLcB/s1600/Capture.jpg)

### Class Loader Subsystem
The class loader goes through steps which involve loading , linking , initialization

Loading Involves storing metadata about the class such as 
method name ,
class name ,
properties of that class etc ..


#### Class Loading Example Program

```
public class Person {  
   private int pId;
   private String pName;
    
   public void setpId(int empId) {
      this.empId = empId;
   }
   public void setPname(String empName) {
      this.empName = empName;
   }
}
```

```
public class Solution {
   public static void main(String[] args) throws ClassNotFoundException {
      Class cl = Class.forName("Person");
      Method[] me = cl.getDeclaredMethods();
      for(Method method : me) {
          System.out.println(method);
      }
      Field[] fi = cl.getDeclaredFields();
      for(Field field : fi) {
          System.out.println(field);
      }
   }
}


```


```
the output :


public void Person.setpId(int)
public void Person.setPname(java.lang.String)
private Person.pId
private java.lang.String Person.pName



```

#### Creation of Class 
After loading is done Jvm creates an object of type java.lang.Class in method area

There are some points to remember 
For unique .class file only one java.lang.Class object will be created 

### Types of ClassLoaders

1)Bootstrap class loader
2)Extension class loader
3)Application class loader

Bootstrap class loader 

It loads classes from bootstrap class path , all the core java classes like String etc..
they are avaiable in rt.jar




Extension class loader

It loads classes from extension class path, it loads classes present in path/ext folder



Application class loader
It loads classes from Application class path , it refers to classes in present application or environment class path


'''
public class Solution {
   public static void main(String[] args) {
       System.out.println(String.class.getClassLoader());
   }
}
'''

output is : 

null

'''



'''

### Other Info
Read more about Linking and  Initialization from 
https://www.javaworld.com/article/2077260/learn-java/learn-java-the-basics-of-java-class-loaders.html