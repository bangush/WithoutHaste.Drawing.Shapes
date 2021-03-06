# [WithoutHaste.Drawing.Shapes](TableOfContents.WithoutHaste.Drawing.Shapes.md).WRangeCircular

**Inheritance:** object → [WShape](WithoutHaste.Drawing.Shapes.WShape.md) → [WRange](WithoutHaste.Drawing.Shapes.WRange.md)  

A range on a circular scale. Immutable.  

**Remarks:**  
A circular scale can be written shorthand as [0, CircularModulus), meaning 0 is included in the scale and CircularModulus is excluded from the scale.  
  
The range may cover the entire scale, or only a portion of the scale.  
To cover the entire scale, set Start and End to the same value.  
  
Throughout the documentation, "scale" refers to the full circular scale [0, CircularModulus) while "range" refers to a subset of values [Start, End].  

# Examples

## Example A:

The degrees of a circle make up a circular scale [0, 360).  
The range may only cover [25, 45] of the scale [0, 360).  
In this case, Start=25, End=45, and CircularModulus=360.  

## Example B:

The hours of a clock make up a circular range [1, 13) for a normal clock, or [0, 24) for a military clock.  
Since RangeCircular always starts at 0, the normal clock would need to be represented as [0, 12). You'd need to handle the +1 offset when setting or displaying values.  

# Fields

## CircularModulus

**readonly int**  

The value at which the range loops back to 0.  

**Remarks:**  
In the context of this range, 0 and CircularModulus are the same value.  

# Properties

## Middle

**double { public get; }**  

Middle value between Start and End.  

## Span

**double { public get; }**  

Distance from Start to End.  

# Constructors

## WRangeCircular(double start, double end, int circularModulus)

**Exceptions:**  
* **[ArgumentException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentexception)**: CircularModulus must be greater than 0.  

# Methods

## Equals(object b)

**virtual bool**  

Circular ranges are equal if they have the same scale and same range, meaning the Start, End, and CircularModulus values are all the same.  

## GetHashCode()

**virtual int**  

## Mod(double number)

**double**  

Convert a number into this scale. Ensures a positive result.  

## Overlaps([WRangeCircular](WithoutHaste.Drawing.Shapes.WRangeCircular.md) b)

**bool**  

Returns true if this range overlaps range _b_.  

## Overlaps(double b)

**virtual bool**  

Returns true if this range includes value _b_.  

**Remarks:**  
_b_ is first put in context of this scale [0, CircularModulus).  
  
For example:  
Value 13 on scale [0, 24) is converted to value 1 when compared to scale [0, 12) because `13 modulus 12 = 1`.  
Value 13 therefore does overlap range [0, 3] on scale [0, 12), but does not overlap range [2, 3] on scale [0, 12).  

# Static Methods

## Centered(double middle, double span, int circularModulus)

**static WRangeCircular**  

**Exceptions:**  
* **[ArgumentException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentexception)**: CircularModulus must be greater than 0.  

## Mod(double number, int m)

**static double**  

Returns _number_ modulus _m_. Ensures a positive result.  

# Operators

## WRangeCircular = WRangeCircular a + WRangeCircular b

Returns a range that covers all the area both _a_ and _b_ cover, including any gap in between.  
If the ranges overlap, there is no gap filled in.  

**Remarks:**  
Gaps are covered from direction _a_ to _b_, therefore this operation is not commutative.  
  Consider range A is [0, 45] on scale [0, 360), and range B is range [90, 180] on scale [0, 360).  
A + B = range [0, 180] on scale [0, 360) which has a Span of 180.  
B + A = range [90, 45] on scale [0, 360) which has a Span of 315.  

**Exceptions:**  
* **[ArgumentException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentexception)**: RangeCirculars with different CircularModulus values cannot be combined.  

## bool = WRangeCircular a == WRangeCircular b

Circular ranges are equal if they have the same scale and same range, meaning the Start, End, and CircularModulus values are all the same.  

## bool = WRangeCircular a != WRangeCircular b

Circular ranges are equal if they have the same scale and same range, meaning the Start, End, and CircularModulus values are all the same.  

