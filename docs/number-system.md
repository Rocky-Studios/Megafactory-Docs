# The Numbering System
**And why standard numbering is flawed**

In C#, your common number types are `int`, `float`, `double`, and `decimal`. These are good for normal programming, and they are easy to use and understand. The Megafactory numbering system addresses some of their flaws:

- Do not support units like litres or cm³

- No easy way to show a number in different notations, eg 123,000,000 as '123 million' or 123 × 10⁶

- No easy way to convert between bases, eg. decimal, binary, ternary, hexadecimal

These problems are all addressed and make coding in the style of this game a lot easier.

The number class is documented [here](API Reference/number.md), but some of its simple use is also explained here.

To create a new number, there are two ways:
## Generating from the constructor
```cs
//                           Numeric value, Unit,             Base
Number myNumber = new Number(10,            NumberUnit.Litre, 10)
```