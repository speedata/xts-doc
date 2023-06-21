# Attribute



Create an attribute for the [Element](../element.md) data structure that can be saved to the hard drive with [SaveDataset](../savedataset.md).



##  Child elements

(none)

##  Parent elements

[Element](../element.md)


## Attributes



`name` (text)
:   Name of the attribute that is created.




`select` ([XPath expressions](../../../manual/xpath.md))
:   The contents of the attribute




## Example

```xml
<Element name="Entry">
  <Attribute name="chapter" select="@name"/>
  <Attribute name="page" select="sd:current-page()"/>
</Element>

```

creates the following structure:


```xml
<Entry chapter="(contents of @name)" page="(the current page number)" />
```





