# Structure of the data file and the layout rules



> You can use any data format so long as it is XML.

## Data source: XML - well-formed and structured

The first prerequisite is that the data source is in XML (Extensible Markup Language) format.
Other formats are not processed with XTS (using the Lua filter, CSV and Excel files can also be processed). In practice, this does not matter because all (structured) data can be converted into XML format.

Often people ask how the data XML must be structured. The answer is simple: there are no specifications, except that the XML must comply with the usual rules (well-formed). These rules are listed in the glossary.

In addition, there are useful structuring recommendations:

1. The data should appear in the XML tree when it is needed. Data processing in XTS costs time and memory, so the information should be available where it is needed. There are of course exceptions. For example, global settings (colors, texts to be translated and so on) can be defined at the beginning of the file.

1. Different representations (variants) must be readable from the data. If, for example, a page change is to occur for a new article group (in the product catalog), a change of article group must be recognizable in the data.

1. The data should be as structured as possible. For example, a product catalog could contain article numbers in the form 123-12345. If the first three digits represent the article group, this could be recognized with regular expressions. It is simpler if the article group is already created in the data structure, so that no recognition is required.

A simple example for the arrangement:

~~~xml
<productdata>
  <globalsettings>
    ...
  </globalsettings>
  <articlegroup name="interior lights" number="123">
    <article number="123-12345">
      <property1>...</property1>
      <property2>...</property2>
    </article>
    <article number="123-12346">
      <property1>...</property1>
      <property2>...</property2>
    </article>
  </articlegroup>
  <articlegroup name="exterior lights" number="124">
    <article number="124-23456">
      <property1>...</property1>
      <property2>...</property2>
    </article>
    <article number="124-54321">
      <property1>...</property1>
      <property2>...</property2>
    </article>
  </articlegroup>
</productdata>
~~~

Redundancy does not hurt here, on the contrary. Since the article group in the example has a clear sequence of digits (123 or 124), the last five digits would be sufficient for the articles. You can assemble the number from `articlegroup/@number`, `-` and `article/@number` yourself. To save yourself the step, simply save the complete number on the article.

To summarize it: If you have the possibility to influence the structure of the data: better save too much information than too little. Experiment with the order of the data, sometimes the right structure makes layout creation much easier.

## How do you access the data from the layout?

Since the data file can be structured as you like, special commands are needed to access the data.
These are described below and in the appendix under [XPath functions](xpath.md). In the following we will start from this simple data file:


~~~xml
<catalog>
  <article nr="12345" price="99,95" quantity="1">
    <description>Text for atricle 12345</description>
    <image mainimage="yes">art12345.pdf</image>
  </article>
  <article nr="56789" price="45,95" quantity="5">
    <description>Text for atricle 56789</description>
    <image>art56789.pdf</image>
  </article>
</catalog>
~~~


This data file is stored under the name `data.xml` so that XTS can find it.

The layout file (name: `layout.xml`) is executed during the import: all commands with the name `<Record>` are saved for later processing, all other commands have immediate effect. This means that if a command like `<DefineColor>` is included at the top level in the layout rules, it will be executed before the actual data processing starts.

A minimum layout file for the data structuring shown above is


~~~xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
  xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

  <Record element="catalog">

  </Record>

</Layout>
~~~


After calling `xts` nothing happens: no page is created, xts simply quits (with an **error**):

~~~
info    Use configuration file xts.cfg
info    XTS start version 0.0.12
info    Creating reproducible build
info    Setup defaults ...
info    Define font family "text"
info    Define font family "sans"
info    Define font family "serif"
info    Define font family "monospace"
info    Define text format "text"
info    Define text format "left"
info    Define text format "right"
info    Define text format "center"
info    Define new page type "default page"
info    Setup defaults ... done
info    Start processing data
Error: no pages in document
~~~


No page is created because no further commands have been specified within the element `<Record>` that cause output.

The structure required for processing is as follows:


~~~xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
  xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

  <Record element="catalog">
    ①
    <ProcessNode select="*"/> ②
    ③
  </Record>

  <Record element="article">
    ④
  </Record>

</Layout>
~~~
① Commands to be executed before the first child elements, e.g. create title page or table of contents (the term child element refers to the data file).<br>
② Here, all child elements are called individually.<br>
③ Commands for closing the PDF file<br>
④ For each child item these commands are executed. The “focus” is now on an article, so you can access the attributes and child elements of articles.

Within the second `<Record>` command (④) you can now access child elements and attributes. Examples:

* `@nr` results in the string 12345 in the first call and 56789 in the second pass.
* `description` results in a sequence with one element, the content text (first article).
* `image/@mainimage` is in the first case the string “yes” (the content of the attribute mainimage), in the second case the empty string “”, because the attribute does not exist there.

For details, see the section on [XPath functions](xpath.md).

Alternatively to the procedure with `<ProcessNode>` and its counterpart `<Record>`, child elements can also be accessed with `<ForAll>`. The following example creates a table line for each child element named article:


~~~xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
  xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

  <Record element="catalog">
    <PlaceObject>
      <Table stretch="max"> ①
        <Tablehead> ②
          <Tr backgroundcolor="gray">
            <Td>
              <Paragraph><Value>Article number</Value></Paragraph>
            </Td>
            </Td>
              <Paragraph><Value>Description</Value></Paragraph>
            </Td>
          </Tr>
        </Tablehead>
        <ForAll select="article"> ③
          <Tr>
            <Td>
              <Paragraph><Value select="@nr"/></Paragraph>
            </Td>
            <Td>
              <Paragraph><Value select="description"/></Paragraph>
            </Td>
          </Tr>
        </ForAll>
      </Table>
    </PlaceObject>
  </Record>
</Layout>
~~~
① A table is output that covers the entire width.<br>
② A table header has the property that it is repeated on every page.<br>
③ Within the `<ForAll>`, the attributes and child elements of each article can be accessed, just like in the example above.

<!-- Tables are covered in the basics (chapter <<ch-intro-tables>>) and in more detail in <<ch-tables2,chapter 6>>. -->


