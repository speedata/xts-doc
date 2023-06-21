# Regular



The (symbolic) name of the fontface for regular text, i.e. without bold or italic.



##  Child elements

(none)

##  Parent elements

[DefineFontfamily](../definefontfamily.md)


## Attributes



`fontface` (text)
:   The symbolic name of the font file.




## Example

```xml
<DefineFontfamily name="Title">
  <Regular fontface="Helvetica Regular"/>
  <Bold fontface="Helvetica Bold"/>
  <Italic fontface="Helvetica Italic"/>
  <BoldItalic fontface="Helvetica Bold Italic"/>
</DefineFontfamily>

```

This font family can now be accessed like this:


```xml
<Textblock fontfamily="Title">
  <Paragraph>
    <Value>...<Value>
  </Paragraph>
</Textblock>

```





