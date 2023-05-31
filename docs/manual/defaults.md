# XTS defaults

XTS defines some default settings that can be changed in the layout file.
These defaults concern the colors, fonts and page size and margins.

## Fonts

~~~xml
<LoadFontfile name="CamingoCode-Bold"        filename="CamingoCode-Bold.ttf" />
<LoadFontfile name="CamingoCode-BoldItalic"  filename="CamingoCode-BoldItalic.ttf" />
<LoadFontfile name="CamingoCode-Italic"      filename="CamingoCode-Italic.ttf" />
<LoadFontfile name="CamingoCode-Regular"     filename="CamingoCode-Regular.ttf" />
<LoadFontfile name="CrimsonPro-Bold"         filename="CrimsonPro-Bold.ttf" />
<LoadFontfile name="CrimsonPro-BoldItalic"   filename="CrimsonPro-BoldItalic.ttf" />
<LoadFontfile name="CrimsonPro-Italic"       filename="CrimsonPro-Italic.ttf" />
<LoadFontfile name="CrimsonPro-Regular"      filename="CrimsonPro-Regular.ttf" />
<LoadFontfile name="TeXGyreHeros-Bold"       filename="texgyreheros-bold.otf" />
<LoadFontfile name="TeXGyreHeros-BoldItalic" filename="texgyreheros-bolditalic.otf" />
<LoadFontfile name="TeXGyreHeros-Italic"     filename="texgyreheros-italic.otf" />
<LoadFontfile name="TeXGyreHeros-Regular"    filename="texgyreheros-regular.otf" />
~~~


The corresponding font family and font size is defined as:

~~~xml
<DefineFontfamily name="text">
  <Regular    fontface="TeXGyreHeros-Regular"/>
  <Bold       fontface="TeXGyreHeros-Bold"/>
  <Italic     fontface="TeXGyreHeros-Italic"/>
  <BoldItalic fontface="TeXGyreHeros-BoldItalic"/>
</DefineFontfamily>

<DefineFontsize name="text" fontsize="10pt" leading="12pt" />
~~~

In both cases the name `text` is used as a default, so you get a 10 point sans font when you do not define anything else.

The font aliases are defined for the default font:

* TeXGyreHeros-Regular → sans-regular
* TeXGyreHeros-Bold → sans-bold
* TeXGyreHeros-Italic → sans-italic
* TeXGyreHeros-BoldItalic → sans-bolditalic
* CrimsonPro-Regular → serif-regular
* CrimsonPro-Bold → serif-bold
* CrimsonPro-Italic → serif-italic
* CrimsonPro-BoldItalic → serif-bolditalic
* CamingoCode-Regular → monospace-regular
* CamingoCode-Bold → monospace-bold
* CamingoCode-Italic → monospace-italic
* CamingoCode-BoldItalic → monospace-bolditalic

## Textformats

The following text formats are predefined:

~~~xml
<DefineTextformat name="text" alignment="justified"/>
<DefineTextformat name="centered" alignment="centered" />
<DefineTextformat name="left" alignment="leftaligned"/>
<DefineTextformat name="right" alignment="rightaligned"/>
~~~

## Page size and margin

The page size defaults to A4 (210mm × 297mm).

The master page for all pages is defined as follows:

~~~xml
<DefineMasterpage name="default page" test="true()" margin="1cm" />
~~~

The page grid is set to 10mm × 10mm.

## Colors

The known CSS colors are defined in the RGB color space. The colors 'black' and 'white' are defined in the grayscale color space. See also the command [`<DefineColor>`](../reference/definecolor.md), there the predefined colors are listed.

The special colors HKS 1-97 and many Pantone colors are already defined with their CMYK values.

