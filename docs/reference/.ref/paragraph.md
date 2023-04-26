# Paragraph



Insert a paragraph of text. The width of the paragraph is inherited from the surrounding element.



##  Child elements

[A](../a.md), [Action](../action.md), [B](../b.md), [Br](../br.md), [I](../i.md), [Span](../span.md), [Value](../value.md)

##  Parent elements

[SetVariable](../setvariable.md), [Td](../td.md), [Textblock](../textblock.md)


## Attributes



`color` (text, optional)
:   Color of the paragraph.




`features` (text, optional)
:   A comma separated list of OpenType features such as +kern,-liga.




`fontfamily` (text, optional, "CSS property": font-family)
:   The name of the font family for the paragraph. The default is “text” (lowercase t).




`textformat` (text, optional)
:   Name of the textformat that is applied to the paragraph. If none is specified the textformat `text` is used.




## Example

```xml
<Textblock>
  <Paragraph fontfamily="Title">
    <Value>Hello World</Value>
  </Paragraph>
</Textblock>

```





