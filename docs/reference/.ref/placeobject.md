# PlaceObject



Outputs a rectangular object (image, table, box, barcode or textblock).



##  Child elements

[Barcode](../barcode.md), [Box](../box.md), [Circle](../circle.md), [Image](../image.md), [Table](../table.md), [Textblock](../textblock.md), [Value](../value.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md)


## Attributes



`allocate` (optional)
:   Determines if the area of the object is marked as “allocated”. With `allocate="no"`, the cursor position is not changed.



    `yes`
    :    Occupy space in the grid (default for grid positioning).



    `no`
    :    Don't allocate space in the grid (default for absolute positioning).




`area` (text, optional)
:   Name of the positioning area where the object should be placed.




`column` (number or length, optional)
:   If contents is a number: the grid cell from the left margin of the area. If it is a length: the absolute position from the left paper margin. If this attribute is omitted, the system tries to place the object by itself.




`groupname` (text, optional)
:   The name of the group that gets output. When given a groupname, PlaceObject should not contain any objects.




`halign` (optional)
:   When an object is placed on the grid and it's width is not a multiple of grid width, there is a space left on the page between the object an the next grid cell. With this attribute you can instruct the software where to place the gap.



    `left`
    :    The object is aligned at the left.



    `right`
    :    The object is aligned to the right.




`hreference` (optional)
:   Determines the placement of the object relative to the given column. If 'left' (which is the default), the given column is the left border of the object. If 'right', the column determines the right edge of the object.



    `left`
    :    The object is placed in given column.



    `right`
    :    The given columns determines the right edge of the border.




`row` (number or length, optional)
:   The row where the object is placed. If none given, the publisher tries to find a row by itself. You can give a number (in grid cells) or an absolute value (from top left).




## Example


Positioning inside the grid:


```xml
<Record element="image">
  <PlaceObject column="12" frame="solid" framecolor="red">
    <Image width="10" file="_samplea.pdf"/>
  </PlaceObject>
</Record>
```

Absolute positioning (from top left edge):


```xml
<Record element="image">
  <PlaceObject column="1cm" row="4cm" frame="solid" framecolor="red">
    <Image width="10" file="_samplea.pdf"/>
  </PlaceObject>
</Record>

```





## Info

The objects can be placed in a grid (when the value in the attributes row and column are numbers) or they can be placed with absolute positions where the origin is at the top and left border of the page.




