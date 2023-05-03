# Record



Contains the instructions when the publisher processes the element in the data file with the given name. The record matching the root element will be called by the software automatically, all further data handling must be done by the user.



##  Child elements

[ClearPage](../clearpage.md), [ForAll](../forall.md), [Group](../group.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [PlaceObject](../placeobject.md), [ProcessNode](../processnode.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Value](../value.md)

##  Parent elements

[Layout](../layout.md)


## Attributes



`element` ([XPath expressions](../../manual/xpath.md))
:   The name of the element the record matches.




`mode` (text, optional)
:   Name of the mode that matches the mode in .




## Example

```xml
<Record element="url" mode="output">
  <PlaceObject>
    <Textblock>
      <Paragraph>
        <A href="https://www.speedata.de"><Value>website of speedata</Value></A>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```





