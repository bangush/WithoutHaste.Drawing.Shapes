# [WithoutHaste.Drawing.Shapes](TableOfContents.WithoutHaste.Drawing.Shapes.md).Geometry

**Static**  
**Inheritance:** object  

Global settings and miscellaneous operations.  

# Enums

**[CoordinatePlanes](WithoutHaste.Drawing.Shapes.Geometry.CoordinatePlanes.md)**  
Determines how cardinal directions apply to coordinates.  

* 0: None  
* 1: Screen  
* 2: Paper  

**[Direction](WithoutHaste.Drawing.Shapes.Geometry.Direction.md)**  
Cardinal directions.  

* 0: None  
* 1: East  
* 2: SouthEast  
* 3: South  
* 4: SouthWest  
* 5: West  
* 6: NorthWest  
* 7: North  
* 8: NorthEast  

# Fields

## CoordinatePlane

**static [CoordinatePlanes](WithoutHaste.Drawing.Shapes.Geometry.CoordinatePlanes.md)**  

This coordinate plane is used in all Shape operations that require one.  

## MarginOfError

**static double**  

When determining equality, all values have a +/- margin of error. This setting is used in all Shape operations that check equality.  

# Properties

## IsCoordinatePlanePaper

**bool { public get; }**  

True if CoordinatePlanes.Paper is selected.  

## IsCoordinatePlaneScreen

**bool { public get; }**  

True if CoordinatePlanes.Screen is selected.  

# Static Methods

## DegreesToRadians(double degrees)

**static double**  

Convert degrees to radians.  

## LineDirection([WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) a, [WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) b)

**static [Direction](WithoutHaste.Drawing.Shapes.Geometry.Direction.md)**  

Given directed line A to B, what direction is it pointing?  

**Remarks:**  
North, South, East, and West answers are exact. So "North" means exactly North.  
The inbetween directions cover all remaining values. So "NorthWest" covers all values between North and West.  

**Exceptions:**  
* **[NotImplementedException](https://docs.microsoft.com/en-us/dotnet/api/system.notimplementedexception)**: Coordinate plane not supported.  

## PointOnLine([WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) a, [WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) b, double distance)

**static [WPoint](WithoutHaste.Drawing.Shapes.WPoint.md)**  

Calculates point along line AB, starting at A and moving towards B  

**Exceptions:**  
* **[ArgumentException](https://docs.microsoft.com/en-us/dotnet/api/system.argumentexception)**: Point A and B cannot be the same.  

## PointPastLine([WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) a, [WPoint](WithoutHaste.Drawing.Shapes.WPoint.md) b, double distance)

**static [WPoint](WithoutHaste.Drawing.Shapes.WPoint.md)**  

Calculates point along line AB, starting at B and moving away from A  

## WithinMarginOfError(double a, double b)

**static bool**  

Check if values are equal, within the MarginOfError.  

# Nested Types

[CoordinatePlanes](WithoutHaste.Drawing.Shapes.Geometry.CoordinatePlanes.md)  
Determines how cardinal directions apply to coordinates.  

[Direction](WithoutHaste.Drawing.Shapes.Geometry.Direction.md)  
Cardinal directions.  

