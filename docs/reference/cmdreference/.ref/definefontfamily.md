# DefineFontfamily



Defines a font family consisting of the shapes “regular”, “bold”, “bold italic” and “italic”. To be used in [Paragraph](../paragraph.md) and [Textblock](../textblock.md) with the attribute `fontfamily`.



##  Child elements

[Bold](../bold.md), [BoldItalic](../bolditalic.md), [Italic](../italic.md), [Regular](../regular.md)

##  Parent elements

[Layout](../layout.md)


## Attributes



`name` (text)
:   The symbolic name that is used as a reference to access this font family.




## Remarks
The default font family is named “text” and it can be redefined by defining a new font family called “text”.

The variants bold, italic and bold italic are optional. 


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





