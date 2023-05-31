# Paragraph



Insert a paragraph of text. The width of the paragraph is inherited from the surrounding element.



##  Child elements

[A](../a.md), [Action](../action.md), [B](../b.md), [Br](../br.md), [I](../i.md), [Ol](../ol.md), [Span](../span.md), [U](../u.md), [Ul](../ul.md), [Value](../value.md)

##  Parent elements

[Case](../case.md), [ForAll](../forall.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [SetVariable](../setvariable.md), [Td](../td.md), [Textblock](../textblock.md), [Until](../until.md), [While](../while.md)


## Attributes



`class` (text, optional)
:   CSS class for this element.




`color` (text, optional)
:   Color of the paragraph.




`features` (text, optional)
:   A comma separated list of OpenType features such as +kern,-liga.




`fontfamily` (text, optional, "CSS property": font-family)
:   The name of the font family for the paragraph. The default is “text” (lowercase t).




`id` (text, optional)
:   CSS id for this element.




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





