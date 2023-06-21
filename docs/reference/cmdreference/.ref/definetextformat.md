# DefineTextformat



Define text formatting instructions. A textformat is used to align and indent text.



##  Child elements

(none)

##  Parent elements

[Layout](../layout.md)


## Attributes



`alignment` (optional)
:   Determines the formatting of the text. It defaults to justified.



    `justified`
    :    Textblock has a rectangular shape.



    `leftaligned`
    :    The text is ragged at the right margin.



    `rightaligned`
    :    The text is ragged right at the left margin.



    `centered`
    :    The text is ragged at the left and the right margin.




`name` (text)
:   Name of the textformat that is used later in the layout.




## Remarks
The textformats `text`, `center`, `left` and `right` are predefined. They stand for justified, centered, left aligned and right aligned text.


## Example

```xml
<DefineTextformat name="text with indentation" alignment="justified" indentation="1cm"/>

<Record element="...">
  <PlaceObject>
    <Textblock textformat="text with indentation">
    <Paragraph>
      <Value>Text ...</Value>
    </Paragraph>
  </Textblock>
  </PlaceObject>
</Record>

```





