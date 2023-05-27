# Textblock



Create a rectangular piece of text.



##  Child elements

[Action](../action.md), [Bookmark](../bookmark.md), [ForAll](../forall.md), [Paragraph](../paragraph.md), [Value](../value.md)

##  Parent elements

[PlaceObject](../placeobject.md), [SetVariable](../setvariable.md)


## Attributes



`fontfamily` (text, optional)
:   The name of the font family. Defaults to `text`.




`fontsize` (text, optional)
:   Set the font size. You can use a name predefined with [DefineFontsize](../definefontsize.md) or a string such as "10pt/12pt" to set the font size and the leading. Defaults to 'text'.




`parsep` (length, optional)
:   The vertical distance between two paragraphs.




`width` (number, optional)
:   Number of columns for the text. If not given, the surrounding element determines the width of the element.




## Example

```xml
<Record element="data">
  <PlaceObject>
    <Textblock width="10" angle="-20">
      <Paragraph>
        <B><Value>Bold slanted text</Value></B>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```





