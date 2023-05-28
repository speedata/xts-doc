# SetVariable



Associates a value with a variable name. The value can be a simple value or a more complex one consisting of several elements.



##  Child elements

[Element](../element.md), [Paragraph](../paragraph.md), [Table](../table.md), [Textblock](../textblock.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Layout](../layout.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes



`select` ([XPath expressions](../../manual/xpath.md), optional)
:   The value of the contents.




`trace` (optional)
:   Show information about the assignment in the log file.



    `yes`
    :    Show information.



    `no`
    :    Don't show information (default).




`variable` (text)
:   The name of the variable that holds the contents.




## Remarks
Variables have global scope.


## Example

```xml
<Record element="product">
  <SetVariable variable="wd" select="5"/>
  <PlaceObject>
    <Textblock width="{ $wd }">
      <Paragraph>
        <Value select="$articlenumber"/>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```

The following example shows a more complex scenario: you can collect complex elements in a variable.


```xml
<Record element="products">
  <SetVariable variable="articletext"/>
  <ProcessNode select="article"/>
  <PlaceObject>
    <Textblock>
      <Value select=" $articletext "/>
    </Textblock>
  </PlaceObject>
</Record>

<Record element="article">
  <SetVariable variable="articletext">
    <!-- the previous contents is added -->
    <Value select="$articletext"/>
    <Paragraph>
      <Value select=" @description "/>
    </Paragraph>
  </SetVariable>
</Record>

```





