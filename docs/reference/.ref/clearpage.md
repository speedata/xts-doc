# ClearPage



Finishes the current page. 



##  Child elements

(none)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes
(none)

## Example

```xml
<Record element="data">
  <PlaceObject>
    <Textblock>
      <Paragraph><Value>This is page 1</Value></Paragraph>
    </Textblock>
  </PlaceObject>
  <ClearPage openon="right"/>
  <PlaceObject>
    <Textblock>
      <Paragraph><Value>And this is page 3</Value></Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```





