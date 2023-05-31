# DefineFontalias



Defines a font alias. When defining a font family, you can use the an alias for the fontname. Aliases are looked up recursively.



##  Child elements

(none)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Layout](../layout.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes



`alias` (text)
:   New (equivalent) name of the font




`existing` (text)
:   The name of the existing font family.




## Example

```xml
<DefineFontalias existing="DejaVuSerif" alias="serif"/>
<DefineFontalias existing="DejaVuSerif-Bold" alias="serif-bold"/>
<DefineFontalias existing="DejaVuSerif-Italic" alias="serif-italic"/>
<DefineFontalias existing="DejaVuSerif-BoldItalic" alias="serif-bolditalic"/>
```

Now you can define a font family with


```xml
<DefineFontfamily name="title" fontsize="15" leading="17">
  <Regular fontface="serif"/>
  <Bold fontface="serif-bold"/>
  <BoldItalic fontface="serif-bolditalic"/>
  <Italic fontface="serif-italic"/>
</DefineFontfamily>
```





