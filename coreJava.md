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

##8. what is class loader in java, and how it works?

Java class loaders are used to load classes at runtime. ClassLoader in Java works on three principle: delegation, visibility and uniqueness

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

##15. what is serialization?





    






