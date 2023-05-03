# Layout



This command is the root element in the Layout instructions.



##  Child elements

[DefineColor](../definecolor.md), [DefineFontfamily](../definefontfamily.md), [DefineFontsize](../definefontsize.md), [DefineMasterpage](../definemasterpage.md), [DefineTextformat](../definetextformat.md), [Function](../function.md), [LoadFontfile](../loadfontfile.md), [Message](../message.md), [Options](../options.md), [PDFOptions](../pdfoptions.md), [Pageformat](../pageformat.md), [Record](../record.md), [SetGrid](../setgrid.md), [SetVariable](../setvariable.md), [Stylesheet](../stylesheet.md), [Trace](../trace.md)

##  Parent elements

(none)


## Attributes



`name` (text, optional)
:   A name for the layout. Optional, without any influence on the layout itself.




`version` (number, optional)
:   Minimum publisher version required. If major or minor version differ, give a warning. Format: 1.6.12 (revision number can be left out).




## Example


This is a complete example for a layout rule set. The first part is the data file (save as `data.xml`) and the second the layout instructions (`layout.xml`).


```xml
<root>
  <elt greeting="Hello world!" />
</root>
```
```xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
  xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

  <Options mainlanguage="English (USA)"/>

  <Record element="root">
    <ProcessNode select="elt"/>
  </Record>

  <Record element="elt">
    <PlaceObject>
      <Textblock>
        <Paragraph>
          <Value select="@greeting"></Value>
        </Paragraph>
      </Textblock>
    </PlaceObject>
  </Record>
</Layout>
```





