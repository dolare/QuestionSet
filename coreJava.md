##1.Implement Singleton in Java

click [here](http://howtodoinjava.com/design-patterns/creational/singleton-design-pattern-in-java/) to see the full version


    public class LazySingleton{
      private static volatile LazySingleton instance = null;
      
      //private constructor
      private LazySingleton(){}
      
      public static LazySingleton getInstance(){
        if(instance == null){
          synchronized(LazySingleton.class){
            //double check
            if(instance == null){
              instance == new LazySingleton();
            }
          }
        }
        return instance;
      }
    }
    
##2. Difference between checked and unchecked exception
click [here](http://beginnersbook.com/2013/04/java-checked-unchecked-exceptions-with-examples/) to see the full version

*how to write a customize exception?*

        package com.javacodegeeks.examples.exception;
        
        public class CustomException extends Exception
        {
        
            private static final long serialVersionUID = 1997753363232807009L;
        
        		public CustomException()
        		{
        		}
        
        		public CustomException(String message)
        		{
        			super(message);
        		}
        
        		public CustomException(Throwable cause)
        		{
        			super(cause);
        		}
        
        		public CustomException(String message, Throwable cause)
        		{
        			super(message, cause);
        		}
        
        		public CustomException(String message, Throwable cause, 
                                                   boolean enableSuppression, boolean writableStackTrace)
        		{
        			super(message, cause, enableSuppression, writableStackTrace);
        		}
        
        }

##3. Difference between Comparable and Comparator

1. Comparator in Java is defined in java.util package while Comparable interface in Java is defined in java.lang package, which very much says that Comparator should be used as an utility to sort objects which Comparable should be provided by default.
2. Comparator interface in Java has method public int compare (Object o1, Object o2) which returns a negative integer, zero, or a positive integer as the first argument is less than, equal to, or greater than the second. While Comparable interface has method public int compareTo(Object o) which returns a negative integer, zero, or a positive integer as this object is less than, equal to, or greater than the specified object.
3. If you see then logical difference between these two is Comparator in Java compare two objects provided to him, while Comparable interface compares "this" reference with the object specified. I have shared lot of tips on how to override compareTo() method and avoid some common mistakes programmer makes while implementing Comparable interface.
4. If any class implement Comparable interface in Java then collection of that object either List or Array can be sorted automatically by using  Collections.sort() or Arrays.sort() method and object will be sorted based on there natural order defined by CompareTo method.

##4. if there is a memory leak in java, how can we locate it?
With Java VisualVM, we can monitor the Java Heap and identify if its behavior is indicative of a memory leak.

##5. Difference between List and Set?
1. Fundamental difference between List and Set in Java is allowing duplicate elements. List in Java allows duplicates while Set doesn't allow any duplicate. If you insert duplicate in Set it will replace the older value. Any implementation of Set in Java will only contains unique elements.
2. Another significant difference between List and Set in Java is order. List is an Ordered Collection while Set is an unordered Collection. List maintains insertion order of elements, means any element which is inserted before will go on lower index than any element which is inserted after. Set in Java doesn't  maintain any order. Though Set provide another alternative called SortedSet which can store Set elements in specific Sorting order defined by Comparable and Comparator methods of Objects stored in Set.
3. Set uses equals() method to check uniqueness of elements stored in Set, while SortedSet uses compareTo() method to implement natural sorting order of elements. In order for an element to behave properly in Set and SortedSet, equals and compareTo must be consistent to each other.
4. Popular implementation of List interface in Java includes ArrayList, Vector and LinkedList. While popular implementation of Set interface includes HashSet, TreeSet and LinkedHashSet.

##6. customize the hashcode and equals method.

        //Hashcode Implementation    
        
           @Override
            public int hashCode() 
            {
                final int prime = 31;
                int result = 1;
                result = prime * result + (isActive ? 1231 : 1237);
                result = prime * result + (wasActive ? 1231 : 1237);
                return result;
            }
        
        //equals Implementation    
            @Override
            public boolean equals(Object obj) 
            {
                if (this == obj)
                    return true;
                if (obj == null)
                    return false;
                if (getClass() != obj.getClass())
                    return false;
                Cell other = (Cell) obj;
                if (isActive != other.isActive)
                    return false;
                if (wasActive != other.wasActive)
                    return false;
                return true;
            }
 
 
##7. hierarchy of sychronization?
  
Synchronization refers to multi-threading. A synchronized block of code can only be executed by one thread at a time.

Java supports multiple threads to be executed. This may cause two or more threads to access the same fields or objects. Synchronization is a process which keeps all concurrent threads in execution to be in synch. Synchronization avoids memory consistence errors caused due to inconsistent view of shared memory. When a method is declared as synchronized; the thread holds the monitor for that method’s object If another thread is executing the synchronized method, your thread is blocked until that thread releases the monitor.

Synchronization in java is achieved using synchronized keyword. You can use synchronized keyword in your class on defined methods or blocks. Keyword can not be used with variables or attributes in class definition.

[useful link here](http://howtodoinjava.com/core-java/multi-threading/thread-synchronization-object-level-locking-and-class-level-locking/)

*Difference between synchronized block and synchronized method*

There two synchronization syntax in Java Language. The practical differences are in controlling scope and the monitor. With a synchronized method, the lock is obtained for the duration of the entire method. With synchronized blocks you can specify exactly when the lock is needed.

The synchronized block can only be executed after a thread has acquired the lock for the object or class referenced, for example the "locker1" or "locker2" in above code, in the synchronized statement.

The above code shows that synchronized block can be holding different object monitors. Maybe it's necessary to protect doSomething1() method and doSomething2() method from multiple threads, but it's fine if one thread is in the doSomething1() method and another is in the doSomething2() method. But the synchronized method can not do it.

A synchronized method synchronizes on the object instance or the class. A thread only executes a synchronized method after it has acquired the lock for the method's object or class.

static synchronized methods synchronize on the class object. If one thread is executing a static synchronized method, all other threads trying to execute any static synchronized methods, in the same class, will block.
non-static synchronized methods synchronize on "this" (the instance object). If one thread is executing a synchronized method, all other threads trying to execute any synchronized methods, in the same class, will block.
These are very public monitors, meaning some other thread could synchronize on them for the wrong reason, leading to slowdowns or deadlocks.

##8. what is class loader in java, and how it works?

Java class loaders are used to load classes at runtime. ClassLoader in Java works on three principle: delegation, visibility and uniqueness.

Java code is compiled into class file by javac compiler and JVM executes Java program, by executing byte codes written in class file. ClassLoader is responsible for loading class files from file system, network or any other source. There are three default class loader used in Java, Bootstrap , Extension and System or Application class loader. 

Read more: http://javarevisited.blogspot.com/2012/12/how-classloader-works-in-java.html#ixzz48vIkTdEd


##9. Difference between string and new String()?

    String s1 = "foobar";
    String s2 = "foobar";

    System.out.println(s1 == s2);      // true

    s2 = new String("foobar");
    System.out.println(s1 == s2);      // false
    System.out.println(s1.equals(s2)); // true
    
![workflow](https://s-media-cache-ak0.pinimg.com/564x/3e/ff/b0/3effb032103f2c88f3c613a57287c79d.jpg)

1. String :String is immutable  ( once created can not be changed )object  . The object created as a String is stored in the  Constant String Pool  . 
Every immutable object in Java is thread safe ,that implies String is also thread safe . String can not be used by two threads simultaneously.

2. StringBuffer:StringBuffer is mutable means one can change the value of the object . The object created through StringBuffer is stored in the heap . StringBuffer  has the same methods as the StringBuilder , but each method in StringBuffer is synchronized that is StringBuffer is thread safe . 

3. StringBuilder:StringBuilder  is same as the StringBuffer , that is it stores the object in heap and it can also be modified . The main difference between the StringBuffer and StringBuilder is that StringBuilder is also not thread safe. 
StringBuilder is fast as it is not thread safe .

##10. what is immutable?

 Immutable class is a class which once created, it’s contents can not be changed. Immutable objects are the objects whose state can not be changed once constructed. e.g. String class
 
 how to create a immutable class?
 1.  create a final class
 2.  set the value of perperties using constractor only
 3.  make the properties of the class final and private
 
 which classes in java are immutable?

All wrapper classes in java.lang are immutable – 
String, Integer, Boolean, Character, Byte, Short, Long, Float, Double, BigDecimal, BigInteger

 What are the advantages of immutability?
 
 1. Immutable objects are automatically thread-safe, the overhead caused due to use of synchronisation is avoided.
 2. Once created the state of the immutable object can not be changed so there is no possibility of them getting into an inconsistent state.
 3. The references to the immutable objects can be easily shared or cached without having to copy or clone them as there state can not be changed ever after construction.
 4. The best use of the immutable objects is as the keys of a map.
 
##11. Difference between HashMap and Hashtable

|---|HashMap|HashTable|
|----|------|--------|
|Synchronized|no|yes|
|Thread-safe|No|Yes|
|null keys and null values|one null key,any null values|not permit null keys and values|
|iterator type|fail fast iterator|fail safe iterator|
|performance|fast|slow|
|superclass and legacy|abstract map,no|dicrionary,yes|

##12. explain weakhashmap

WeakHashMap is an implementation of Map interface where the memory of the value object can be reclaimed by Grabage Collector if the corresponding key is no longer referred by any section of program. This is different from HashMap where the value object remain in HashMap even if key is no longer referred. We need to explicitly call remove() method on HashMap object to remove the value so that it can be ready to be reclaimed(Provided no other section of program refers to that value object). Calling remove() is an extra overhead.

##13. what is generic?

“Java Generics” is a technical term denoting a set of language features related to the definition and use of generic types and methods . In java, Generic types or methods differ from regular types and methods in that they have type parameters.

“Java Generics are a language feature that allows for definition and use of generic types and methods.”
Generic types are instantiated to form parameterized types by providing actual type arguments that replace the formal type parameters. A class like LinkedList<E> is a generic type, that has a type parameter E . Instantiations, such as LinkedList<Integer> or a LinkedList<String>, are called parameterized types, and String and Integer are the respective actual type arguments.

##14. what is the diiference between hashSet and LinkedHashSet?

[go to this link to see detail](http://javaconceptoftheday.com/hashset-vs-linkedhashset-vs-treeset-in-java/)

##15. Explain serialization?

Object Serialization in Java is a process used to convert Object into a binary format which can be persisted into disk or sent over network to any other running Java virtual machine; the reverse process of creating object from binary stream is called deserialization in Java.


*how to make a Java class serializable?*
Making a class Serializable in Java is very easy, Your Java class just needs to implements java.io.Serializable interface and JVM will take care of serializing object in default format

*What is the difference between Serializable and Externalizable interface in Java?*
Externalizable provides us writeExternal() and readExternal() method which gives us flexibility to control java serialization mechanism instead of relying on Java's default serialization. Correct implementation of Externalizable interface can improve performance of application drastically.

*How many methods Serializable has? If no method then what is the purpose of Serializable interface?*
Serializable interface exists in java.io package and forms core of java serialization mechanism. It doesn't have any method and also called Marker Interface in Java. When your class implements java.io.Serializable interface it becomes Serializable in Java and gives compiler an indication that use Java Serialization mechanism to serialize this object.

*What is serialVersionUID? What would happen if you don't define this?*

SerialVersionUID is an ID which is stamped on object when it get serialized usually hashcode of object, you can use tool serialver to see serialVersionUID of a serialized object . SerialVersionUID is used for version control of object. you can specify serialVersionUID in your class file also. Consequence of not specifying serialVersionUID is that when you add or modify any field in class then already serialized class will not be able to recover because serialVersionUID generated for new class and for old serialized object will be different. Java serialization process relies on correct serialVersionUID for recovering state of serialized object and throws java.io.InvalidClassException in case of serialVersionUID mismatch, to learn more about serialversionuid see this article.

*While serializing you want some of the members not to serialize? How do you achieve it?*

Another frequently asked Serialization interview question. This is sometime also asked as what is the use of transient variable, does transient and static variable gets serialized or not etc. so if you don't want any field to be part of object's state then declare it either static or transient based on your need and it will not be included during Java serialization process.

Read more: http://javarevisited.blogspot.com/2011/04/top-10-java-serialization-interview.html#ixzz48wNcHpIH


##16. what is autoboxing?please give an example?

When Java automatically converts a primitive type like int into corresponding wrapper class object e.g. Integer than its called autoboxing  because primitive is boxed into wrapper class while in opposite case is called unboxing, where an Integer object is converted into primitive int. All primitive types e.g. byte, short, char, int, long, float, double and boolean has corresponding wrapper class e.g. Byte, Short, Integer, Character etc and participate in autoboxing and unboxing. Since the whole process happens automatically without writing any code for conversion its called autoboxing and auto-unboxing

![example](https://4.bp.blogspot.com/-go-bemNoIPc/VXhMH26751I/AAAAAAAAC-w/ZutSedwa1UM/s640/Autoboxing%2Band%2BUnboxing%2Bin%2BJava%2B2.jpg)

Read more: http://javarevisited.blogspot.com/2012/07/auto-boxing-and-unboxing-in-java-be.html#ixzz48wPG3cvP

##17. what is reflection and how to use it?

Java Reflection is a process of examining or modifying the run time behavior of a class at run time.

The java.lang.Class class provides many methods that can be used to get metadata, examine and change the run time behavior of a class.

Java Reflection is quite powerful and can be very useful. Java Reflection makes it possible to inspect classes, interfaces, fields and methods at runtime, without knowing the names of the classes, methods etc. at compile time. It is also possible to instantiate new objects, invoke methods and get/set field values using reflection.

examle:

    Method[] methods = MyObject.class.getMethods();
     for(Method method : methods){
        System.out.println("method = " + method.getName());
    }
This example obtains the Class object from the class called MyObject. Using the class object the example gets a list of the methods in that class, iterates the methods and print out their names.

##18. explain thread life cycle?

A thread can be in one of the five states. According to sun, there is only 4 states in thread life cycle in java new, runnable, non-runnable and terminated. There is no running state.

![life cycle image](https://s-media-cache-ak0.pinimg.com/564x/8c/62/46/8c6246c6585ecd0a0ad11a9d89295e68.jpg)

1. New

The thread is in new state if you create an instance of Thread class but before the invocation of start() method.

2. Runnable

The thread is in runnable state after invocation of start() method, but the thread scheduler has not selected it to be the running thread.

3. Running

The thread is in running state if the thread scheduler has selected it.

4. Non-Runnable (Blocked)

This is the state when the thread is still alive, but is currently not eligible to run.

5. Terminated

A thread is in terminated or dead state when its run() method exits.

##19. List methods in class Object

1. protected Object clone()
2. boolean equals(Object obj)
3. protected void finalize()
4. Class<?> getClass()
5. int hashCode()
6. void notify()
7. void notifyAll()
8. String toString()
9. void wait()


##20. What is Collection hierachy in Java?
![image](https://s-media-cache-ak0.pinimg.com/564x/6b/2f/c1/6b2fc16a7a0e4979e6970596b0d74ab0.jpg)

![image](https://s-media-cache-ak0.pinimg.com/564x/c1/50/df/c150df332d3dc7cfe66d33235d1653ba.jpg)

![image](https://s-media-cache-ak0.pinimg.com/564x/68/c8/a4/68c8a479d489c0b65f3e3586bbf8298f.jpg)

different between collection and collections?

First of all, "Collection" and "Collections" are two different concepts. As you will see from the hierarchy diagram below, "Collection" is a root interface in the Collection hierarchy but "Collections" is a class which provide static methods to manipulate on some Collection types.


##21 New features in Java 1.7 and Java 1.8?

1.8:Language changes:

lambda expressions (JSR 335, includes method handles)
continuation of Project Coin (small language improvements)
annotations on Java types
Library changes:

Improved Date and Time API

1.7:Language changes:

Project Coin (small changes)
switch on Strings
try-with-resources
diamond operator
Library changes:

new abstracted file-system API (NIO.2) (with support for virtual filesystems)
improved concurrency libraries
elliptic curve encryption
more incremental upgrades
Platform changes:

support for dynamic languages

##22. what is the difference between interface and abstract class?

|interface|abstract class|
|---------|---------------|
|Interface can have only abstract methods.|Abstract class can have abstract and non-abstract methods.|
| Interface supports multiple inheritance.|Abstract class doesn't support multiple inheritance.|
|Interface has only static and final variables.|Abstract class can have final, non-final, static and non-static variables.|
|Interface can't have static methods, main method or constructor.|Abstract class can have static methods, main method and constructor.|
|Interface can't provide the implementation of abstract class.|Abstract class can provide the implementation of interface.|
|The interface keyword is used to declare interface.| The abstract keyword is used to declare abstract class.|

##23










    






