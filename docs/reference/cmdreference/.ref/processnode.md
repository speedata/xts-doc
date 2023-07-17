# ProcessNode



Executes all given nodes. The elements, that are to be executed, are given with the attribute `selection`.



##  Child elements

(none)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes



`limit` (number, optional)
:   Limits the number of items processed with this command




`mode` (text, optional)
:   Name of the mode. This must match the mode at the corresponding [Record](../record.md) element. With this it is possible to have different rules for the same element.




`select` ([XPath expressions](../../../manual/xpath.md))
:   Selection of child elements, that are to be processed.




## Example

```xml
<ProcessNode select="*" mode="sum" />
```





