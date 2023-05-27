# Value



Contains a text value that is passed to the surrounding element.



##  Child elements

(none)

##  Parent elements

[A](../a.md), [AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [B](../b.md), [Columns](../columns.md), [Contents](../contents.md), [Function](../function.md), [I](../i.md), [Message](../message.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [Record](../record.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Span](../span.md), [Table](../table.md), [Td](../td.md), [Textblock](../textblock.md), [Tr](../tr.md), [U](../u.md)


## Attributes



`select` ([XPath expressions](../../manual/xpath.md), optional)
:   Value to be passed to the outer element.




## Remarks
The value can be passed to the outer element either as an XPath expression or as the contents of this element.

Containing Br-tags will be interpreted as newlines.


## Example

```xml
<Record element="data">
  <PlaceObject>
   <Textblock>
     <Paragraph>
       <Value select="@name"/><Value>, symbol=</Value><Value select="@symbol"/>
     </Paragraph>
   </Textblock>
  </PlaceObject>
</Record>

```





