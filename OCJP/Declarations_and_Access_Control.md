### Declarations and Access Control

##### Java Features and Benefits

- [ ] OO
- [ ] Encapsulation
- [ ] Automatic memory management
- [ ] A large API
- [ ] Built-in security features
- [ ] Multiplatform compatibility
- [ ] Strong typing
- [ ] Multithreading
- [ ] Distributed computing

##### Class Modifiers (Nonaccess)

- [ ] Classes can be modified with `final`, `abstract`, or `strictfp`

- [ ] A class cannot be both `final` and `abstract`

- [ ] An abstract class can have both `abstract` and nonabstract methods

##### Interface Implementation

- [ ] Usually, interfaces are contracts for what a class can do, but they say nothing about the way in which the class must do it

- [ ] Interfaces can be implemented by any class from any inheritance tree

- [ ] Usually, an interface is like a 100 percent `abstract` class and is implicitly `abstract` whether or not you type the `abstract` modifier in the declaration

- [ ] Interfaces methods are by default `public` and usually `abstract`--explicit declaration of these modifiers is optional

- [ ] Interfaces can have constants, which are always implicitly `public`, `static` and `final`

- [ ] Interface constant declarations of `public`, `static` and `final` are optional in any combination

- [ ] As of Java 8, interfaces can have concrete methods declared as either `static` or `default`

- [ ] A legal nonabstract implementing class has the following properties: 

  - It provides concrete implementations for the interface's methods

  - It must follow all legal override rules for the methods it implements
  - It must not declare any new checked exceptions for an implementation method
  - It may declare runtime exceptions on any interface method implementation
  - It must maintain the exact signature and return type of the methods it implements (but does not have declare the exceptions of the interface) 
  - A class implementing an interface can itself be abstract
  - Interfaces can extend one or more other interfaces
  - Interfaces cannot extend a class or implement a class or interface

- [ ] A class implementing an interface can itself be `abstract`

##### Member Access Modifiers

- [ ] `private` members are not visible to subclasses, so `private` members cannot be inherited
- [ ] Default members can be accessed only by classes in the same package
- [ ] `protected` members can be accessed by other classes in the same package, plus subclasses, regardless of package
- [ ] A subclass outside the package cannot access a `protected` member by using a reference to a superclass instance (the `protected` member can only be accessed through inheritance)
- [ ] A `protected` member inherited by a subclass from another package is not accessible to any other class in the subclass package, except for the subclass's own subclasses

##### Other Modifiers

- [ ] The `synchronized` modifier applies only to methods and code blocks.
- [ ] `synchronized` methods can have any access control and can also be marked `final`
- [ ] `abstract` methods must be implemented by a subclass, so they must be inheritable, they cannot be `private` or `final`
- [ ] The `native` modifier applies only to methods
- [ ] The `strictfp` modifier applies only to methods and classes

##### Variable Declarations

- [ ] Instance variables can have any access control, and can be marked `final` or `transient`
- [ ] Instance variables can't be `abstract`, `synchronized`, `native` or `strictfp`
- [ ] It is legal to declare a local variable with the same name as an instance variable, it is called "shadowing"
- [ ] `final` variables must be initialized before the constructor completes
- [ ] There is no such thing as a final object.
- [ ] The `volatile` and `transient` modifier applies only to instance variables
- [ ] An array of objects can hold any object that passes the IS-A (or `instanceof`) test for the declared type of the array. For example, if `Horse` extends `Animal`, then a `Horse` object can go into an `Animal` array.

##### enums

- [ ] An `enum` can be declared inside or outside a class, but not in a method
- [ ] An `enum` declared outside the class cannot be marked static, final, abstract, protected or private
- [ ] An `enum` can contain constructors, methods, variables, and constant-specific class bodies
- [ ] `enum` constants can send arguments to the `enum` constructor, using the syntax `BIG(8)`, where `int` literal 8 is passed to the `enum` constructor
- [ ] `enum` constructors can have arguments and can be overloaded
- [ ] `enum` constructors cannot be invoked directly in code. They are always called automatically when an `enum` is initialized
- [ ] The semicolon at the end of an `enum` declaration is optional.
- [ ] `MyEnum.values()` returns an array of `MyEnum`'s values