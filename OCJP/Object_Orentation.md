Object Orentation

##### Encapsulation, IS-A, HAS-A

- [ ] IS-A refers to inheritance or implementation
- [ ] IS-A is expressed with the keyword `extends` or `implements`
- [ ] HAS-A means an instance of one class "has a" reference to an instance of another class or another instance of the same class

##### Polymorphism

- [ ] A reference variable is always of a single, unchangeable type, but it can refer to a subtype object
- [ ] A single object can be referenced to by reference variables of many different types--as long as they are the same type or supertype of the object
- [ ] The reference variable's type (not the object's type) determines which method can be called

##### Overriding and Overloading

- [ ] Constructors can be overloaded but not overridden
- [ ] With respect to the method it overrides, the overriding method
  - must have the same argument list
  - must have the same return type or a subclass (known as a covariant return)
  - must not have a more restrictive access modifier
  - may have a less restrictive access modifier
  - must not throw new or broader checked exceptions
  - may throw new or narrower checked exceptions, or any unchecked exceptions
- [ ] Only inherited methods can be overridden, and private methods are not inherited
- [ ] A subclass uses *super.overriddenMethodName()* to call the superclass version of an overridden method
- [ ] A subclass uses *MyInterface.super.overriddenMethodName()* to call the super interface version of an overridden method
- [ ] Overloaded method
  - must have different argument list
  - may have different return type, as long as the argument list is also different
  - may have different access modifier
  - may throw different exceptions
- [ ] Methods from a supertype can be overloaded in a subtype 
- [ ] Object type determines which overridden method is used at runtime
- [ ] Reference type determines which overloaded method will be used at compile time

##### Reference Variable Casting

- [ ] Downcasting means casting down the inheritance tree to a more specific type
- [ ] Before trying the downcast, do an `instanceof` test to make sure
- [ ] Must make an explicit cast to do the donwcasting
- [ ] Upcasting means casting up the inheritance tree to a more general type
- [ ] Upcasting works implicitly because when doing upcasting, the number of methods which can be invoked are implicitly restricted
- [ ] Upcasting is an inherently safe operation because the assignment restricts the access capabilities of the new variable

##### Return Types

- [ ] Overloaded methods can change return types, overridden methods cannot, except in the case of covariant returns
- [ ] Methods with an object reference return type can return a subtype
- [ ] Methods with an interface return type can return any implementer

##### Constructors and Instantiation

- [ ] The default constructor is a no-arg constructor with a no-arg call to *super()*
- [ ] The first statement of every constructor must be a call either to *this()* (an overloaded constructor) or to *super()*
- [ ] Instance members are accessible only after the `super` constructor runs
- [ ] Abstract classes have constructors that are called when a concrete subclass is instantiated
- [ ] Interfaces do not have constructors
- [ ] If your super class does not have a no-arg constructor, you must create a constructor and insert a call to *super()* with arguments matching those of the superclass constructor
- [ ] Constructors are not inherited, thus they cannot be overridden
- [ ] A constructor can be directly invoked only by another constructor (using a call to *super()* or *this()*)
- [ ] Constructors can call constructors, but one of them must call *super()* or the stack will explode
- [ ] Call to *this()* and *super()* cannot be in the same constructor

##### Initialization Blocks

- [ ] *init* blocks execute in the order in which they appear
- [ ] Static *init* blocks run once, when the class is first loaded
- [ ] Instance *init* blocks run every time a class instance is created
- [ ] Instance *init* blocks run after the constructor's call to *super()*

##### statics

- [ ] Use the dot operator to access `static` members, but remember that using a reference variable with the dot operator is really a  syntax trick, and the compiler will substitute the class name for the reference variable
- [ ] `static` methods cannot be overridden, but they can be redefined