##1. What is $scope（What is the relationship between $scope and controller?）

Scope is a special javascript object which plays the role of joining controller with the views. Scope contains the model data.
In controllers, model data is accessed via $scope object.

##2. What is $watch, $digest, $apply and what are the situations we use them?

The $scope.watch() function creates a watch of some variable.

The $scope.$digest() function iterates through all the watches in the $scope object, and its child $scope objects (if it has any)]

The $scope.$apply() function takes a function as parameter which is executed, and after that $scope.$digest() is called internally. 
That makes it easier for you to make sure that all watches are checked, and thus all data bindings refreshed.

##3. Difference between Service, Factory, Provider and Value

##4. what is $injector?

$injector is used to retrieve object instances as defined by provider, instantiate types, invoke methods, and load modules.

##5. filter in angular?

A filter formats the value of an expression for display to the user. They can be used in view templates, controllers or services and it
is easy to define your own filter.

##6. life cycle of angulrJS?

1. create scope
The root scope is created by the $injector when the application is bootstrapped.

2.  watcher registration
This phase registers watches for values on the scope that are represented in the template. 

3. Model mutation
This phase occurs when data in the scope changes. When you make the changes in your angular app code, the e function $apply() updates the model and calls the $digest() function to update the DOM elements and registered watches.
