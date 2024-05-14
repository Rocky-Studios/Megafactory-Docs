# The Numbering System
**And why standard numbering is flawed**

In C#, your common number types are `int`, `float`, `double`, and `decimal`. These are good for normal programming, and they are easy to use and understand, but they have a few problems and limitations. The Megafactory numbering system addresses some of their flaws:

- Do not support units like litres or cm³

- No easy way to show a number in different notations, eg 123,000,000 as '123 million' or 123 × 10⁶

- No easy way to convert between bases, eg. decimal, binary, ternary, hexadecimal

These problems are all addressed and make coding in the way that I do a lot easier.

The number class is documented [here](API Reference/number.md), but some of its simple use is also explained here.

To create a new number, there are two ways:
## Generating from the constructor
```cs
Number myNumber = new Number(
  "10",                                       // Numeric Value (0, 1, 2, -1, 21, -52)
  measurementType = MeasurementType.Length,   // Measurement type (Length, volume, speed, area)
  numberUnit = NumberUnit.Centimeter,         // Unit of the measurement type (Meter, Centimeter, Foot)
  base = 10);                                 // Base of the counting system (2 -> binary,
  //                                             3 -> ternary, 10 -> decimal, 16 -> hexadecimal)
```
!!! note "Some things to note"
    The numberic value takes a string so it can parse different bases eg. hexadecimal is 0-9-A-F.

    Measurement type is an optional value and defaults to `MeasurementType.PlainNumber` when not assigned. Same with unit, which defaults to `NumberUnit.PlainNumber`.

    Base is optional and defaults to 10.

## Generating from a string
```cs
Number myNumber = Number.FromString("10cm Length b10");
//                                   numbericvalueUnit Type bBase 
```

## Returning the number
When getting the value of your number, there are many options
```cs
double myNumberPlain               = myNumber.Get(NumberOutput.Plain);     // 10
string myNumberUnits               = myNumber.Get(NumberOutput.Unit);      // 10cm
string myNumberUnitType            = myNumber.Get(NumberOutput.UnitType)   // 10cm Length
string myNumberBase                = myNumber.Get(NumberOutput.Base)       // 10 b10
string myNumberUnitBase            = myNumber.Get(NumberOutput.UnitBase)   // 10cm b10
string myNumberFull                = myNumber.Get(NumberOutput.Full)       // 10cm Length b10
string myNumberScientific          = myNumber.Get(NumberOutput.Scientific) // 1 x 10^1
string myNumberScientificUnicode   = myNumber.Get(NumberOutput.Scientific) // 1 × 10¹
```