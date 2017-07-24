# Trait linearization
* left to right construction i.e pushing on to the stack, right overrides left
* Each trait is constructed only once so if a trait has already appeared as a subtype of other trait it is not *constructed* again
```scala
B <: D and C <: D
val instance = new A extends B with C
```
D is constructed only once when constructing B. Linearization order is `CBDA' 

## General Tips
* Use parameter less def to describe value , allows deriving classes/traits more flexibility as to how they want to override it i.e val, def or lazy val ...

### Override rules
* val: Override only with val
* lazy val: Override only with lazy val (note that base val will not be initialized when constructing derived class)
This can be confusing because vals in base classes are part of constructor code and are intitalized. lazy vals are too but the initialization is prevented by a boolean check.
* var: No overrides allowed.
* def: All except var can override
