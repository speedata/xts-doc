# AtPageCreation



The contents of the element [AtPageCreation](../atpagecreation.md) is executed the first time the page is accessed. This is used in [DefineMasterpage](../definemasterpage.md).



##  Child elements

[ClearPage](../clearpage.md), [DefineFontalias](../definefontalias.md), [ForAll](../forall.md), [Group](../group.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [PlaceObject](../placeobject.md), [ProcessNode](../processnode.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[DefineMasterpage](../definemasterpage.md)


## Attributes
(none)

## Example

```xml
<AtPageCreation>
  <PlaceObject column="1" row="1">
    <Textblock>
      <Paragraph>
        <Value select="$pageheader"/>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</AtPageCreation>

```





