### Object Orientation

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

### Test

##### Q1

```java
class Clidder {
    private final void flipper() {
        System.out.println("Clidder");
    }
}
public class OCJP extends Clidder {
    public final void flipper() {
        System.out.println("Clidlet");
    }
    public static void main (String[] args) {
        new OCJP().flipper();
    }
}
```

What is the result?

A: 

```
Childlet
```

Although a final method cannot be overridden, in this case, the method is private and, therefore, hidden. The effect is that a new, accessible method *flipper*() is created.

If the modifier of  *flipper*()  in class *Clidder* was changed into `public`, then the compilation would fail.

##### Q2

```java
class Bird {
    { System.out.println("b1 "); }
    public Bird() { System.out.println("b2 "); }
}

class Raptor extends Bird {
    static { System.out.println("r1 "); }
    public Raptor() { System.out.println("r2 "); }
    { System.out.println("r3 "); }
    static { System.out.println("r4 "); }
}

class Hawk extends Raptor {
    public static void main (String[] args) {
        System.out.println("pre ");
        new Hawk();
        System.out.println("hawk ");
    }
}
```

What is the result?

A: 

```
r1 r4 pre b1 b2 r3 r2 hawk
```

##### Q3

```java
class X { void do1() { } }

class Y extends X { void do2() { } }

class Chrome {
    public static void main(String[] args) {
        X x1 = new X ();
        X x2 = new Y ();
        Y y1 = new Y ();
        // insert code here
    }
```

Which of the following will compile?

```
A. x2.do2();
```

```
B. (Y)x2.do2();
```

```
C. ((Y)x2.do2());
```

```
D. None of the above statements will compile
```

A: C

Before you can invoke *Y*'s *do2()* method, you have to cast *x2* to be of type *X*.

B looks like a proper cast, but without the second set of parentheses, the compiler think it's an incomplete statement.

##### Q4

```java
class Dog {
    public void bark() { System.out.println("woof "); }
}

class Hound extends Dog {
    public void sniff() {
        System.out.println("sniff ");
    }
    public void bark() {
        System.out.println("howl ");
    }
}

class DogShow {
    public static void main(String[] args) { new DogShow().go(); }
    void go() {
        new Hound().bark();
        ((Dog) new Hound()).bark();
        ((Dog) new Hound()).sniff(); // line 19
    }
}
```

What is the result?

A:  Compilation fails with an error at line 19

Class *Dog* doesn't have a *sniff()* method. If line 19 is commented, the output will be: 

```
howl
howl
```

##### Q5

```java
class Tree { }

class Redwood extends Tree {
    public static void main(String[] args) { new Redwood().go(); }
    void go() {
        go2(new Tree(), new Redwood());
        go2((Redwood) new Tree(), new Redwood());
    }
    void go2(Tree t1, Redwood r1) {
        Redwood r2 = (Redwood)t1;
        Tree t2 = (Tree)r1;
    }
}
```

What is the result?

A: An exception is thrown at runtime

```
java.lang.ClassCastException: Tree cannot be cast to Redwood
```

The code would work if it's like this: 

```java
class Tree { }

class Redwood extends Tree {
    public static void main(String[] args) { new Redwood().go(); }
    void go() {
        go2(new Tree(), new Redwood());
        //go2((Redwood) new Tree(), new Redwood());
    }
    void go2(Tree t1, Redwood r1) {
        
        // false
        if (t1 instanceof Redwood){
            Redwood r2 = (Redwood)t1;
        }
        //Redwood r2 = (Redwood)t1;
        Tree t2 = (Tree)r1;
    }
}
```

##### Q6

```java
interface MyInterface {
    default int doStuff() {
        return 0;
    }
}

class IfaceTest implements MyInterface {
    public static void main (String[] args) {
        new IfaceTest().go();
    }

    void go() {
        // INSERT CODE HERE;
    }

    public int doStuff() {
        return 0;
    }
}
```

Which line(s) of code, inserted independently at // INSERT CODE HERE, will allow the code to compile?

A: 

```
System.out.println("class: " + doStuff());
System.out.println("iface: " + MyInterface.super.doStuff());
```

The second line of code is the correct syntax to invoke the interface's overloaded `default` method.

Another code that can compile:

```java
interface MyInterface {
    static int doStuff() {
        return 0;
    }
}

class IfaceTest implements MyInterface {
    public static void main (String[] args) {
        new IfaceTest().go();
    }

    void go() {
        // INSERT CODE HERE;
        System.out.println("class: " + doStuff());
        System.out.println("iface: " + MyInterface.doStuff());
    }

    public int doStuff() {
        return 0;
    }
}
```

