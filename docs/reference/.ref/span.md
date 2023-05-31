# Span



Surround text by styling options.



##  Child elements

[A](../a.md), [Action](../action.md), [B](../b.md), [Br](../br.md), [I](../i.md), [Ol](../ol.md), [Span](../span.md), [U](../u.md), [Ul](../ul.md), [Value](../value.md)

##  Parent elements

[A](../a.md), [B](../b.md), [I](../i.md), [Li](../li.md), [Paragraph](../paragraph.md), [Span](../span.md), [U](../u.md)


## Attributes



`class` (text, optional)
:   CSS class for this element.




`id` (text, optional)
:   CSS id for this element.




`style` (text, optional)
:   Set the CSS style.




## Example

```xml
<Stylesheet>
  .green { background-color: lightgreen; }
</Stylesheet>

<Record element="data">
  <PlaceObject>
    <Textblock>
      <Paragraph>
        <Span class="green"><Value>green</Value></Span>
      </Paragraph>
    </Textblock>
  </PlaceObject>
</Record>

```





