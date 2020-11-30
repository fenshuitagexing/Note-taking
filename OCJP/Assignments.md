## Assignments

### 1 Key points

##### 1.1 Basic Assignments

- [ ] Floating-point numbers are implicitly doubles
- [ ] Narrowing a primitive truncates the high order bits
- [ ] Compound assignments (such as +=) perform an automatic cast
- [ ] underscores can be included in numeric literals, but not at the beginning or the end.

##### 1.2 Initialization

- [ ] When an array of objects is instantiated, objects within the array are instantiated automatically, but all the reference get the default value of `null`
- [ ] When an array of primitives is instantiated, elements get default values
- [ ] Instance variables are always initialized with a default value

##### 1.3 Garbage Collection

- [ ] Objects must be considered eligible before they can be garbage collected
- [ ] An object is eligible when no live thread can reach it
- [ ] Islands of objects can be garbage collected, even though they refer to each other

### 2 Test

##### Q1

```java
class CardBorad {
    Short story = 200;
    CardBorad go(CardBorad cb) {
        cb = null;
        return cb;
    }
    
    public static void main (String[] args) {
        CardBorad c1 = new CardBorad();
        CardBorad c2 = new CardBorad();
        CardBorad c3 = c1.go(c2);
        c1 = null;
        // do stuff
    }
}
```

When *// do stuff* is reached, how many objects are eligible for garbage collection?

A: 2

*c1* has an associated `Short` wrapper object which is also eligible.

##### Q2

```java
class Ouch {
    static int ouch = 7;
    public static void main (String[] args) {
        new Ouch().go(ouch);
        System.out.println(" " + ouch);
    }
    void go(int ouch) { // line 9
        ouch++;
        for (int ouch = 3; ouch < 6; ouch++); // line 11
        System.out.println(" " + ouch);
    }
}
```

What is the result?

A: Compilation fails

The declaration on line 9 is valid (although ugly), but the variable name *ouch* cannot be declared again on line 11 in the same scope as the declaration on line 9.

##### Q3

```java
class Beta { }
class Alpha {
    static Beta b1;
    Beta b2;
}
class Tester {
    public static void main (String[] args) {
        Beta b1 = new Beta();       Beta b2 = new Beta();
        Alpha a1 = new Alpha();     Alpha a2 = new Alpha();
        a1.b1 = b1;
        a1.b2 = b1;
        a2.b2 = b2;
        a1 = null;  b1 = null;  b2 = null;
        // do stuff
    }
}
```

When *// do stuff* is reached, how many objects will be eligible for garbage collection?

A: 1

It should be clear that there is still a reference to the object referred to  by *a2*

And there is still a reference to the object referred to by *a2.b2*

What might be less clear is that you can still access the other *Beta* object through the static variable *a2.b1*