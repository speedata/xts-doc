# Message



Writes a message onto the console and to the protocol file.



##  Child elements

[Element](../element.md), [Value](../value.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Layout](../layout.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Tr](../tr.md)


## Attributes



`errorcode` (number, optional)
:   If an error is raised, use this code on exit. Defaults to 1. Negative values are reserved for system purpose.




`exit` (optional)
:   Tells the software to exit immediately.



    `no`
    :    The speedata Publisher continues with the PDF creation.



    `yes`
    :    The speedata Publisher exits without finishing the PDF file.




`select` ([XPath expressions](../../manual/xpath.md), optional)
:   Contents of the message. You can alternatively specify the message by the child elements [Value](../value.md).




`type` (optional)
:   The type of the message.



    `error`
    :    Report an error.



    `warning`
    :    Report a warning.



    `debug`
    :    Report a debug message.



    `info`
    :    Report an information (default).




## Example






