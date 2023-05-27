# A



Insert hyperlink to a URL.



##  Child elements

[A](../a.md), [Action](../action.md), [B](../b.md), [Br](../br.md), [I](../i.md), [Span](../span.md), [U](../u.md), [Value](../value.md)

##  Parent elements

[A](../a.md), [B](../b.md), [I](../i.md), [Paragraph](../paragraph.md), [Span](../span.md), [U](../u.md)


## Attributes



`href` (text, optional)
:   The target of the hyperlink (URI). Example: `https://www.speedata.de`




`link` (text, optional)
:   The target of the document link (a Mark). Example: `article123`




## Example

```xml
<PlaceObject>
  <Textblock>
    <Paragraph><Value>See the </Value>
      <A href="https://www.speedata.de">
        <Value>homepage</Value>
      </A>
      <Value> for more information.</Value>
    </Paragraph>
  </Textblock>
</PlaceObject>
```





