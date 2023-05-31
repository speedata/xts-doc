# Value



Contains a text value that is passed to the surrounding element.



##  Child elements

(none)

##  Parent elements

[A](../a.md), [AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [B](../b.md), [Case](../case.md), [Columns](../columns.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [I](../i.md), [Li](../li.md), [Loop](../loop.md), [Message](../message.md), [Otherwise](../otherwise.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [Record](../record.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Span](../span.md), [Table](../table.md), [Td](../td.md), [Textblock](../textblock.md), [Tr](../tr.md), [U](../u.md), [Until](../until.md), [While](../while.md)


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





