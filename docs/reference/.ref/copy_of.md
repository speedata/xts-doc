# Copy-of



Replace this element by the copy of the selection as an element structure. You can use it to construct more complex data structures.



##  Child elements

(none)

##  Parent elements

[Columns](../columns.md), [SaveDataset](../savedataset.md), [Table](../table.md), [Td](../td.md), [Textblock](../textblock.md), [Tr](../tr.md)


## Attributes



`select` ([XPath expressions](../../manual/xpath.md))
:   The selection (most likely a variable) that is to be copied.




## Example

```xml
<SetVariable variable="myparagraph">
  <Paragraph>
    <Value select="@name"/><Value>, Symbol=</Value><Value select="@symbol"/>
  </Paragraph>
</SetVariable>
<PlaceObject>
  <Textblock>
    <Copy-of select="$myparagraph"/>
  </Textblock>
</PlaceObject>

```

is the same as


```xml
<PlaceObject>
  <Textblock>
    <Paragraph>
      <Value select="@name"/><Value>, Symbol=</Value><Value select="@symbol"/>
    </Paragraph>
  </Textblock>
</PlaceObject>
```

with the exception that the values of `@name` and `@symbol` can be evaluated before the text gets output.







