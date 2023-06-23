# Textblock



Create a rectangular piece of text.



##  Child elements

[Action](../action.md), [Bookmark](../bookmark.md), [ForAll](../forall.md), [Paragraph](../paragraph.md), [Value](../value.md)

##  Parent elements

[PlaceObject](../placeobject.md), [SetVariable](../setvariable.md)


## Attributes



`parsep` (length, optional)
:   The vertical distance between two paragraphs.




`width` (number, optional)
:   Number of columns for the text. If not given, the surrounding element determines the width of the element.




## Example

```xml
<Record element="data">
  <PlaceObject>
    <Textblock width="10">
      <Paragraph>
        <B><Value>Bold text</Value></B>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```





