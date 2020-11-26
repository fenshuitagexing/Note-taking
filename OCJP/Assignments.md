Assignments

##### Basic Assignments

- [ ] Floating-point numbers are implicitly doubles
- [ ] Narrowing a primitive truncates the high order bits
- [ ] Compound assignments (such as +=) perform an automatic cast

##### Initialization

- [ ] When an array of objects is instantiated, objects within the array are instantiated automatically, but all the reference get the default value of `null`
- [ ] When an array of primitives is instantiated, elements get default values
- [ ] Instance variables are always initialized with a default value

##### Garbage Collection

- [ ] Objects must be considered eligible before they can be garbage collected
- [ ] An object is eligible when no live thread can reach it
- [ ] Islands of objects can be garbage collected, even though they refer to each other
