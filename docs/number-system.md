# The Numbering System
**And why standard numbering is flawed**

In C#, your common number types are `int`, `float`, `double`, and `decimal`. These are good for normal programming, and they are easy to use and understand, but they have a few problems and limitations. The Megafactory numbering system addresses some of their flaws:

- Do not support units like litres or cm³

- No easy way to show a number in different notations, eg 123,000,000 as '123 million' or 123 × 10⁶

- No easy way to convert between bases, eg. decimal, binary, ternary, hexadecimal

These problems are all addressed and make coding in the way that I do a lot easier.

The number class is documented [here](API Reference/number.md), but some of its simple use is also explained here.

## Number Types
Here is all the measurement types supported:
(The metric system is clearly superior so only that is supported)

**Length:**
Millimetres, Centimetres, Metres, Kilometres

**Area:**
Millimetres², Centimetres², Metres², Kilometres², Hectares

**Volume:**
Millimetres³, Centimetres³, Metres³, Kilometres³, Millilitres, Litres, Kilolitres

**Speed:**
Millimetres/second, Centimetres/second, Metres/second, Kilometres/hour

**Temperature:**
Celsuis, Kelvin

**Angles:**
Degrees, Radians

**Mass:**
milligrams, grams, kilograms, tonnes

**Density:**
milligrams/mm³, grams/cm³, kilograms/m³

## Generating numbers
To create a new number, there are two ways:

(also, the only units that can be negative are speed, degrees, radians, and °celsius)
### Generating from the constructor
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

### Generating from a string
```cs
Number myNumber = Number.Parse("10cm Length b10");
//                              numbericvalueUnit Type bBase 
```

## Returning the number
When getting the value of your number, there are many options
```cs
double myNumberPlain               = myNumber.GetPlain();       // 10
string myNumberUnits               = myNumber.GetUnit();        // 10cm
string myNumberUnitType            = myNumber.GetUnitType();    // 10cm Length
string myNumberBase                = myNumber.GetBase();        // 10 b10
string myNumberUnitBase            = myNumber.GetUnitBase();    // 10cm b10
string myNumberFull                = myNumber.GetFull();        // 10cm Length b10
string myNumberScientific          = myNumber.GetScientific();  // 1 x 10^1
string myNumberScientificUnicode   = myNumber.GetScientificU(); // 1 × 10¹
```

## Conversions


## Math
### Addition and subtraction
One of the main reasons I decided to reinvent how computers handle numbers is addition or subtraction with different units of measurement.

If you have two numbers, `numberA` and `numberB`, both of which are length, in normal code you would just add them like this:
```cs
numberA + numberB;
```

But what if they have different units? What if numberA is in millimetres and numberB is in centimeters? Well, there's no way to tell and this could get confusing quickly. So if you tried to do this with the new number system, you would get an error:
!!! failure "Error"
    Operand '+' is not supported between types of Number and Number.

Instead to add numbers, you need to do it like this:
```cs
Number.Add(numberA, numberB, NumberUnit.Centimeter);
```
Notice the inclusion of a third value, the desired NumberUnit. The add function will automatically handle the conversions and you'll get the desired output. If the numbers have different MeasurementTypes, it will throw an error:
!!! failure "Error"
    Math encountered incompatible units.
This also works the same for subtraction.

### Multiplication and Division
Multiplication and division are slightly different,

??? note "Rules"
    **Multiplication**

    You multiply two lengths, you get area.

    You multiplty an area by a length, you get volume.

    But if you multiple Area by Area or Volume by anything, you'll get 4D space, which is not something I'm ready for just yet.
    
    **Division**

    You divide area by length, you get length.

    You divide volume by area, you get length.

    You divide volume by length, you get area.


Other than that, it works the same:
```cs
//              10cm     5m       outputs: 0.5m²
Number.Multiply(numberA, numberB, NumberUnit.Metre);

//              10cm     50m²     outputs: 5m³
Number.Multiply(numberA, numberB, NumberUnit.Metre);
```
The general rule is, *does it make logical sense to do this?*

## Conclusion
Numbers in normal programming are good for just that, *normal programming*, but in specialised cases, you may find yourself having to change key features of something to better fit what you are doing. It is recommended that you use this system only where necessary.

I that this system, which in my opinion is quite useful in certain fields of programming, should not be restricted to this game. That's why it's available online at its [Github page](https://github.com/Rocky-Studios/Number-System). <br>It is open source and free, so use it in your projects, modify it to your needs and contribute if you have an idea.