# Td



Td wraps a table cell, just like HTML.



##  Child elements

[Bookmark](../bookmark.md), [Box](../box.md), [ForAll](../forall.md), [Image](../image.md), [Loop](../loop.md), [Paragraph](../paragraph.md), [Switch](../switch.md), [Table](../table.md), [Value](../value.md)

##  Parent elements

[Tr](../tr.md)


## Attributes



`class` (text, optional)
:   The css class to be used for formatting the table cell.




`colspan` (number, optional)
:   The number of columns for this cell. Defaults to 1.




`id` (text, optional)
:   CSS id for this table cell.




`rowspan` (number, optional)
:   The number of rows for this cell. Defaults to 1.




`style` (text, optional)
:   CSS style for this table cell.




## Remarks
The child elements of the table cells are either block objects that start a new line or inline objects that are placed horizontally next to each other (from left to right) until the width of the table cell forces a line break.
        Block objects are [Paragraph](../paragraph.md), [Table](../table.md) and [Box](../box.md), inline objects are [Barcode](../barcode.md) and [Image](../image.md).


## Example


The following example places a background text behind the Td cell.


```xml

<Record element="data">
   <PlaceObject>
     <Table stretch="yes">
       <Columns>
         <Column width="5cm"/>
       </Columns>
       <Tr>
         <Td>
           <Paragraph><Value>A wonderful serenity has taken possession of my entire soul,
             like these sweet mornings of spring which I enjoy with my whole heart.</Value>
           </Paragraph>
         </Td>
       </Tr>
     </Table>
   </PlaceObject>
</Record>

```





