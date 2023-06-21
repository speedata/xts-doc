# Element



Create a data structure that can be used to save on the hard-drive between consecutive runs (with [SaveDataset](../savedataset.md)).



##  Child elements

[Attribute](../attribute.md), [Element](../element.md)

##  Parent elements

[Element](../element.md), [Message](../message.md), [SaveDataset](../savedataset.md), [SetVariable](../setvariable.md)


## Attributes



`name` (text)
:   Name of the element that gets created.




## Example

```xml
<SetVariable variable="articles">
  <Element name="articlelist">
    <Attribute name="name" select=" @name "/>
    <Attribute name="page" select="sd:current-page()"/>
  </Element>
</SetVariable>

```





