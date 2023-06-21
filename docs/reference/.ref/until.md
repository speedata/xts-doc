# Until



Create a loop. All child elements are executed repeatedly until the given condition is true. The return value of Until is the concatenated return value of the child elements.



##  Child elements

[ClearPage](../clearpage.md), [Column](../column.md), [DefineFontalias](../definefontalias.md), [Li](../li.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [SetVariable](../setvariable.md), [Until](../until.md), [While](../while.md)


## Attributes



`test` ([XPath expressions](../../manual/xpath.md))
:   Every time after the the loop is executed, the condition is evaluated. If it is true, the loop exits.




## Example

```xml
<Record element="data">
  <SetVariable variable="i" select="0"/>
  <Until test="$i = 4">
    <Message select="concat('$i is: ', $i)"/>
    <SetVariable variable="i" select="$i + 1"/>
  </Until>
</Record>

```

Gives the following output (in the protocol file)


```xml
Message: "$i is: 0.000000"
Message: "$i is: 1.000000"
Message: "$i is: 2.000000"
Message: "$i is: 3.000000"
```





