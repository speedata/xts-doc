# Bold



Name of the font face that should be used when switching to “bold”.



##  Child elements

(none)

##  Parent elements

[DefineFontfamily](../definefontfamily.md)


## Attributes



`fontface` (text)
:   Name of the font for bold.




## Example

```xml
<LoadFontfile name="Times" filename="timesregular.otf"/>
<LoadFontfile name="Times bold" filename="timesbold.otf"/>
<LoadFontfile name="Times italic" filename="timesitalic.otf"/>
<LoadFontfile name="Times bold italic" filename="timesbolditalic.otf"/>

<DefineFontfamily name="text">
  <Regular fontface="Times"/>
  <Bold    fontface="Times bold"/>
  <Italic  fontface="Times italic"/>
  <BoldItalic fontface="Times bold italic" />
</DefineFontfamily>

```





