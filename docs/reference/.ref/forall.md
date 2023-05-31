# ForAll



Executes the given commands for all elements in the data XML file that match the contents of the attribute `select`.



##  Child elements

[ClearPage](../clearpage.md), [Column](../column.md), [DefineFontalias](../definefontalias.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Columns](../columns.md), [Contents](../contents.md), [DefineMasterpage](../definemasterpage.md), [Function](../function.md), [Ol](../ol.md), [Record](../record.md), [SaveDataset](../savedataset.md), [Td](../td.md), [Textblock](../textblock.md), [Tr](../tr.md), [Ul](../ul.md)


## Attributes



`limit` (number, optional)
:   Limits the number of children to the given number.




`select` ([XPath expressions](../../manual/xpath.md))
:   Selects the child elements from the data XML




`start` (number, optional)
:   The first entry to process. Default is 1.




## Example

```xml
<Record element="data">
  <PlaceObject>
    <Table>
      <ForAll select="entry">
        <Tr><Td><Paragraph><Value select="string(.)"/></Paragraph></Td></Tr>
      </ForAll>
    </Table>
  </PlaceObject>
</Record>
```

Creates a table row for all elements `entry` in the data element `data`. The data XML should look similar to this:


```xml
<data>
  <entry>a</entry>
  <entry>b</entry>
  <entry>c</entry>
</data>
```





