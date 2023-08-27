## Schema validation

A special feature of the speedata Publisher is that the input language is formulated in XML. Compared to other programming languages, XML is "chatty": You always have to write end tags for the start tags:

~~~xml
<PlaceObject>
   ...
</PlaceObject>
~~~

Compared to a C-like syntax like

~~~go
placeObject(...)
~~~


this is more typing. The solution to this “problem” is to use a text editor that is good with XML.
For example, entering a start tag would immediately insert the end tag.
Or, if the tag name was changed, both the start tag and the end tag would be changed at the same time.
Good XML editors do much more than just make it easier to enter tags, for example, to validate code against a schema.

## What is a schema?

A schema (e.g. XML-Schema or [RELAX NG](https://de.wikipedia.org/wiki/RELAX_NG)) contains information about the permitted structure of an XML file. For example, the schema that is supplied with the speedata Publisher contains the following information:

*  The root element must be called `<Layout>`
*  The child element of `<PlaceObject>` must be either `<Barcode>`, `<Box>`, `<Circle>`, `<Frame>`, `<Image>`, `<Rule>`, `<Table>` or `<Textblock>`.
* The attribute `valign` in the table row can be one of the values `top`, `middle`, or `bottom`.
*  and many more


The documentation of the individual commands and the selection options is also included in the supplied schematic.
A good XML editor can import such a schema and make it much easier for the user to enter the source code.
Coding with a good schema is a lot of fun and has some advantages over the classic text editor:

* Syntax errors are displayed immediately
* Commands (tags) do not have to be entered completely, because the editor offers an auto-complete function
* The attributes are immediately checked for meaningful values
* Documentation is available directly in the editor
* ... basically what you expect from an integrated development environment (IDE).

29 autocomplete1
Selection of allowed child elements
29 autocomplete2
Allowed attributes for text block
#Integration of the schemata

## Associate XML editor with schema

Most XML editors can provide useful input support with RELAX NG schema or with XML schema (see Schema validation).

The idea is basically always the same: either you assign a schema file to the speedata namespace (`urn:speedata.de/2021/xts/en`) in principle, or you link each file to the schema separately.

* [Visual Studio Code](vscode.md)
* [OxygenXML](oxygenxml.md)
