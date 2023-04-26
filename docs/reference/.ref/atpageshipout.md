# AtPageShipout



The enclosed instructions will be executed when the page is placed into the PDF file. Used in [DefineMasterpage](../definemasterpage.md).



##  Child elements

[ClearPage](../clearpage.md), [ForAll](../forall.md), [Group](../group.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [PlaceObject](../placeobject.md), [ProcessNode](../processnode.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md)

##  Parent elements

[DefineMasterpage](../definemasterpage.md)


## Attributes
(none)

## Example

```xml
<AtPageShipout>
  <PlaceObject column="1" row="20">
    <Textblock>
      <Paragraph>
        <Value select="sd:current-page()"/>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</AtPageShipout>

```





