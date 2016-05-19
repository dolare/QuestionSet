##1. differenece between BeanFactory and ApplicationContext?

Both BeanFactory and ApplicationContext provides a way to get a bean from Spring IOC 
container by calling getBean("bean name")

1.  BeanFactory doesn't provide support for internationalization 
2. One of the popular implementation of BeanFactory interface is XMLBeanFactory while one of 
the popular implementation of ApplicationContext interface is ClassPathXmlApplicationContext.
3. If you are using auto wiring and using BeanFactory than you need to register AutoWiredBeanPostProcessor using API which you can configure in XML if you are using  ApplicationContext. In summary BeanFactory is OK for testing and non production use but ApplicationContext is more feature rich container implementation and should be favored over BeanFactory

##2. How does Spring instantiate a bean? Different ways to configure a bean

constructor injection and properties injection

##3. spring scope

|scope| description|
|-----|------------|
|singleton|This scopes the bean definition to a single instance per Spring IoC container |
|prototype|This scopes a single bean definition to have any number of object instances.|
|request|This scopes a bean definition to an HTTP request. Only valid in the context of a web-aware Spring ApplicationContext.|
|session|This scopes a bean definition to an HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.|
|global session|This scopes a bean definition to a global HTTP session. Only valid in the context of a web-aware Spring ApplicationContext.|


##4. how to do injection in spring?
xml configuration file and annotation

##5. what is lazy loading in spring?
A bean is loaded only when an instance of that Java class is requested by any other method or a class. -

##6. what is the difference between two ways of dependecy injection?

1. Setter injection in Spring uses setter methods like setDependency() to inject dependency on any bean managed 
by Spring's IOC container. On the other hand constructor injection uses constructor to inject dependency on any 
Spring-managed bean.

2. .......

##7. in which situation you use constructor injection instead of setter injection?

Use Setter injection when a number of dependencies are more or you need readability. 
Use Constructor Injection when Object must be created with all of its dependency.
(immutable class doesnot have setter method)

##8. the worklow of spring MVC?

1.  First request will be received by DispatcherServlet
2.  DispatcherServlet will take the help of HandlerMapping and get to know the Controller class name associated
with the given request.
3.  So request transfer to the Controller, and then controller will process the request by executing appropriate methods and returns
ModeAndView object (contains Model data and View name) back to the DispatcherServlet
4.  Now DispatcherServlet send the model object to the ViewResolver to get the actual view page
5.  Finally DispatcherServlet will pass the Model object to the View page to display the result

##9. 3 mapping ways in spring mvc?

1. @requestmapping
2. @modelattrubute
3. viewresolver


##10. what is aop and how to use it in detail?

Aspect-oriented programming, or AOP, is a programming technique that allows programmers to modularize crosscutting concerns, or behavior
that cuts across the typical divisions of responsibility, such as logging and transaction management. 

advice types:before advice,around advice, after returning advice,after advice,after throwing advice.


##11. spring trasaction management?
Spring Framework supports:
Programmatic transaction management. 
Declarative transaction management.


##12. 




