# While



Create a loop. All child elements are executed as long as the condition in the test attribute evaluates to true.



##  Child elements

[ClearPage](../clearpage.md), [Column](../column.md), [Li](../li.md), [LoadDataset](../loaddataset.md), [Loop](../loop.md), [Message](../message.md), [NextFrame](../nextframe.md), [NextRow](../nextrow.md), [Paragraph](../paragraph.md), [PlaceObject](../placeobject.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md), [Switch](../switch.md), [Until](../until.md), [Value](../value.md), [While](../while.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [SetVariable](../setvariable.md), [Until](../until.md), [While](../while.md)


## Attributes



`test` ([XPath expressions](../../../manual/xpath.md))
:   Every time before the the loop is executed, this condition must evaluate to true. See the command [Until](../until.md) for a loop with an exit test.




## Example


The following example creates a textblock with three times the contents 'Text Text Text '.


```xml

<Record element="data">
    <SetVariable variable="counter" select="1"/>
    <SetVariable variable="text" select="''"/>
    <While test=" $counter &lt;= 3 "> <!-- less or equal -->
        <SetVariable variable="counter" select=" $counter + 1"/>
        <SetVariable variable="text">
            <Value select="$text"/>
            <Value select="'Text '"/>
      </SetVariable>
    </While>
    <PlaceObject>
        <Textblock>
            <Paragraph><Value select="$text"/></Paragraph>
        </Textblock>
    </PlaceObject>
</Record>

```





