# Td



Td wraps a table cell, just like HTML.



##  Child elements

[Bookmark](../bookmark.md), [Box](../box.md), [ForAll](../forall.md), [Image](../image.md), [Loop](../loop.md), [Paragraph](../paragraph.md), [Switch](../switch.md), [Table](../table.md), [Value](../value.md)

##  Parent elements

[Tr](../tr.md)


## Attributes



`align` (optional, "CSS property": text-align)
:   Horizontal alignment of the cell contents. Defaults to left.



    `left`
    :    The contents is left aligned (ragged right). This is the default.



    `right`
    :    The contents of the cell is right aligned.



    `center`
    :    The contents of the cell is aligned at the center, with ragged right and left margin.



    `justify`
    :    Justified text with straight margins.




`background-font-family` (text, optional, "CSS property": background-font-family)
:   Set the font family of the background text. Defaults to the table font.




`background-size` (optional, "CSS property": background-size)
:   Controls the size of the background text. Currently only 'contain' and 'auto' is allowed.



    `contain`
    :    Fill the height of the table cell.



    `auto`
    :    The background text is not scaled.




`background-text` (optional, "CSS property": background-text)
:   A text that should be placed in the background of the table cell.




`background-textcolor` (optional, "CSS property": background-textcolor)
:   The color of the text in the background (if any).




`background-transform` (optional, "CSS property": background-transform)
:   The transformation of the background text (if any). Currently supported: `rotate(-40deg)` (and other angles in the range 0 to -90).




`backgroundcolor` (text, optional, "CSS property": background-color)
:   The name of the background color (if the cell should get a background).




`border-bottom` (length, optional, "CSS property": border-bottom-width)
:   The width (thickness) of the bottom border. The border is inside the cell.




`border-bottom-color` (text, optional, "CSS property": border-bottom-color)
:   The color of the bottom border.




`border-left` (length, optional, "CSS property": border-left-width)
:   The width (thickness) of the left border. The border is inside the cell.




`border-left-color` (text, optional, "CSS property": border-left-color)
:   The color of the left border.




`border-right` (length, optional, "CSS property": border-right-width)
:   The width (thickness) of the right border. The border is inside the cell.




`border-right-color` (text, optional, "CSS property": border-right-color)
:   The color of the left border.




`border-top` (length, optional, "CSS property": border-top-width)
:   The width (thickness) of the top border. The border is inside the cell.




`border-top-color` (text, optional, "CSS property": border-top-color)
:   The color of the top border.




`class` (text, optional)
:   The css class to be used for formatting the table cell.




`colspan` (number, optional)
:   The number of columns this cell spans. Defaults to 1.




`graphics` (text, optional)
:   Draw the predefined MetaPost graphic around the table cell (experimental).




`id` (text, optional)
:   CSS id for this table cell.




`padding` (length, optional, "CSS property": padding)
:   Shorthand for setting padding-top and the other values with this length.




`padding-bottom` (length, optional, "CSS property": padding-bottom)
:   Set the inner distance (width between contents and the border) to the bottom edge.




`padding-left` (length, optional, "CSS property": padding-left)
:   Set the inner distance (width between contents and the border) to the left edge.




`padding-right` (length, optional, "CSS property": padding-right)
:   Set the inner distance (width between contents and the border) to the right edge.




`padding-top` (length, optional, "CSS property": padding-top)
:   Set the inner distance (width between contents and the border) to the top edge.




`rotate` (number, optional)
:   Rotate the contents of the table cell. Positive values return clockwise. This is experimental and currently only for text.




`rowspan` (number, optional)
:   The number of rows for this cell. Defaults to 1.




`valign` (optional, "CSS property": vertical-align)
:   The vertical alignment of the cell.



    `top`
    :    The contents is aligned at the top edge of the cell.



    `middle`
    :    The contents is vertically centered.



    `bottom`
    :    The contents is aligned at the bottom edge of the cell.




## Remarks
The child elements of the table cells are either block objects that start a new line or inline objects that are placed horizontally next to each other (from left to right) until the width of the table cell forces a line break.
        Block objects are [Paragraph](../paragraph.md), [Table](../table.md) and [Box](../box.md), inline objects are [Barcode](../barcode.md) and [Image](../image.md).


## Example


The following example places a background text behind the Td cell.


```xml
<DefineFontfamily name="td-background" fontsize="12" leading="12">
  <Regular fontface="TeXGyreHeros-Bold"/>
</DefineFontfamily>

<Record element="data">
   <PlaceObject>
     <Table stretch="yes">
       <Columns>
         <Column width="5cm"/>
       </Columns>
       <Tr>
         <Td border-top="0.25pt" border-bottom="0.25pt"
            background-text="hello!"
            background-textcolor="goldenrod"
            background-transform="rotate(-30deg)"
            background-size="contain"
            background-font-family="td-background">
           <Paragraph><Value>A wonderful serenity has taken possession of my entire soul,
             like these sweet mornings of spring which I enjoy with my whole heart.</Value>
           </Paragraph>
         </Td>
       </Tr>
     </Table>
   </PlaceObject>
</Record>

```





