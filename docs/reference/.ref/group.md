# Group



Create a virtual page that behaves like a real page but is not placed into the PDF.



##  Child elements

[Contents](../contents.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Contents](../contents.md), [Record](../record.md)


## Attributes



`name` (text)
:   Name of the group that is created.




## Example

```xml
<Record element="data">
  <Group name="Some group">
    <!-- Optional, taken from the current page -->
    <Grid width="10mm" height="10mm"/>
    <Contents>
      <PlaceObject column="3" row="2">
        <Textblock width="14">
          <Paragraph>
            <Value>Text</Value>
          </Paragraph>
        </Textblock>
      </PlaceObject>
      <PlaceObject column="2" row="4">
        <Textblock width="14">
          <Paragraph>
            <Value>Next text</Value>
          </Paragraph>
        </Textblock>
      </PlaceObject>
    </Contents>
  </Group>
  <PlaceObject groupname="Some group" row="1" />
</Record>

```





