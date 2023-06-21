# Function



Define a function



##  Child elements

[ClearPage](../clearpage.md), [Column](../column.md), [Columns](../columns.md), [ForAll](../forall.md), [Group](../group.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [Param](../param.md), [PlaceObject](../placeobject.md), [ProcessNode](../processnode.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Value](../value.md)

##  Parent elements

[Layout](../layout.md)


## Attributes



`name` (text, optional)
:   The name of the function (with namespace prefix).




## Example

```xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
    xmlns:sd="urn:speedata.de/2021/xtsfunctions/en"
    xmlns:fn="mynamespace"
    >

  <Record element="data">
    <PlaceObject>
        <Textblock>
            <Paragraph>
                <Value select="fn:add(3,4)"></Value>
            </Paragraph>
        </Textblock>
    </PlaceObject>
</Record>

...

<Function name="fn:add">
    <Param name="a" />
    <Param name="b" />
    <Value select="$a + $b" />
</Function>

```

Print out the number 7.







