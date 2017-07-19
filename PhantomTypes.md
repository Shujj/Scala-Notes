# Phantom types
lets start with haskell example which is unsurprisingly clearer than corresponding scala version.
A phantom type is a parametrised type whose parameters do not all appear on the right-hand side of its definition.
```haskell
data Ratio n = Ratio Double
1.234 :: Ratio D3

data Ask ccy = Ask Double
Ask 1.5123 :: Ask GBP
```
In the above example the second type parameter is phantom , the motivation being to "diff" b/w two doubles
The diff b/w two return types allows the compiler to enforce more strict checks rendering some undesirable/invalid states inrepresentable.
[SO question about phantom types in Haskell](https://stackoverflow.com/questions/28247543/motivation-behind-phantom-types)
> Normal algebraic data types in Haskell allow you to choose the type of the arguments of a data constructor. However, it doesn't allow you to choose the return type of a data constructor.

Hmm a bit confused , is such a contraint enforced in scala ? I mean case class T constructor/apply has to return object of type T 

```scala
case class Ratio(ratio: Double)
case class Ask(ask: Double)

val ratio = Ratio(14.6)
val ask = Ask(134.55)

val unintended = ask.ask + ratio.ratio
println(unintended)
```
Ok above can be prevented using path dependent types but that is too strict since we still want to allow addition of `ask` from two different insances of `Ask`.




