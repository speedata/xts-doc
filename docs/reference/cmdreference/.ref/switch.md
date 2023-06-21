# Switch



Create an if-then-else construct. The test attribute of each [Case](../case.md) commands is evaluated until it yields true. The contents of the Case gets executed. If no test succeeds, the (optional) [Otherwise](../otherwise.md) gets executed.



##  Child elements

[Case](../case.md), [Otherwise](../otherwise.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Columns](../columns.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [PositioningArea](../positioningarea.md), [Record](../record.md), [Td](../td.md), [Tr](../tr.md), [Until](../until.md), [While](../while.md)


## Attributes
(none)

## Example

```xml
<Record element="data">
  <SetVariable variable="counter" select="3"/>
  <Switch>
    <Case test=" $counter &lt; 5">
      <SetVariable variable="text" select="'Less than 5'"/>
    </Case>
    <Case test=" $counter &lt; 20">
      <SetVariable variable="text" select="'Less than 20'"/>
    </Case>
    <Otherwise>
      <SetVariable variable="text" select="'Larger or equal to 20'"/>
    </Otherwise>
  </Switch>
  <PlaceObject>
    <Textblock>
      <Paragraph><Value select="$text"/></Paragraph>
    </Textblock>
  </PlaceObject>
</Record>
```





## Info

You have to be careful to encode the test with the rules of XML: that is “less” must be written as `\&lt;`, since `<` must not be part of text contents.



A Switch may be part of nearly all commands. It dissolves and only the contents of the Case or Otherwise gets replaced by the whole construct.




