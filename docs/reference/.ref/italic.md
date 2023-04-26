# Italic



The font face to be used when the user switches to italic.



##  Child elements

(none)

##  Parent elements

[DefineFontfamily](../definefontfamily.md)


## Attributes



`fontface` (text)
:   The name of the fontface.




## Example

```xml
<LoadFontfile name="Helvetica" filename="helvetica-regular.otf"/>
<LoadFontfile name="Helvetica Bold" filename="helvetica-bold.otf"/>
<LoadFontfile name="Helvetica Italic" filename="helvetica-italic.otf"/>
<LoadFontfile name="Helvetica Bold Italic" filename="helvetica-bolditalic.otf"/>

<DefineFontfamily name="text" >
  <Regular fontface="Helvetica"/>
  <Bold fontface="Helvetica Bold"/>
  <Italic fontface="Helvetica Italic"/>
  <BoldItalic fontface="Helvetica Bold Italic"/>
</DefineFontfamily>

```





