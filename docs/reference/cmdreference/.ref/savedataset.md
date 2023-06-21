# SaveDataset



Saves an element/attribute structure to be used in the next publisher run. The contents must have a tree structure.



##  Child elements

[Element](../element.md), [ForAll](../forall.md), [Loop](../loop.md), [Value](../value.md)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes



`attributes` ([XPath expressions](../../../manual/xpath.md), optional)
:   The variable (as an XPath expression, e.g. `$foo`) which contains [Attribute](../attribute.md) Elements. These attributes are added to the root element.




`elementname` (text)
:   Name of the root element that surrounds the elements given by the child elements.




`href` (text, optional)
:   Name of the file. Example: toc.xml




`name` (text, optional)
:   Name of the file. Example: toc




`select` ([XPath expressions](../../../manual/xpath.md), optional)
:   Alternative to giving the data structure in the child elements.




## Example

```xml
  <Record element="data">
    <SetVariable variable="attributesvar">
      <Attribute name="att1" select="'Hello'" />
      <Attribute name="att2" select="123" />
    </SetVariable>

    <SaveDataset name="toc" elementname="root" attributes="$attributesvar">
      <Element name="child">
        <Attribute name="attchild" select="999"/>
      </Element>
    </SaveDataset>
  </Record>

```

This code saves an XML file to the disc which has this structure:


```xml
<root att1="Hello" att2="123">
 <child attchild="999"/>
</root>

```





