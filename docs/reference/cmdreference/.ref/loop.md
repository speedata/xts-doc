# Loop



Repeat the contents of this element several times.



##  Child elements

[ClearPage](../clearpage.md), [Column](../column.md), [Li](../li.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [ProcessNode](../processnode.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Tr](../tr.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Columns](../columns.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [SaveDataset](../savedataset.md), [Table](../table.md), [Td](../td.md), [Tr](../tr.md), [Until](../until.md), [While](../while.md)


## Attributes



`select` ([XPath expressions](../../../manual/xpath.md))
:   The number of loops. Must be a number or castable as a number.




`variable` (text, optional)
:   If given, store the current loop value in this variable. If omitted, the loop value is stored in the variable `_loopcounter`.




## Example

```xml
<PlaceObject>
  <Table>
    <Loop select="5" variable="i">
      <Tr>
        <Td><Paragraph><Value select="$i"/></Paragraph></Td>
      </Tr>
    </Loop>
  </Table>
</PlaceObject>

```





