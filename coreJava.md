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
            
