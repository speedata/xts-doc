# XPath expressions


Attributes `select` and `test` expect an XPath expression to get the data. For example the test in a Switch/Case statement must evaluate to `true()` or `false()`:

```xml
<SetVariable variable="a" select="1234"/>
...
<Switch>
    <Case test="$a > 12">
        ...
    </Case>
</Switch>
```

or the contents of a variable is set like this:

```xml
<SetVariable variable="foo" select="data"/>
```

This selects the child elements of the current node in the data file with the name data. See an XPath 2 introduction for more information on XPath (for example on [W3Schools](https://www.w3schools.com/xml/xpath_intro.asp)).

All other attributes in the layout file allow a temporary XPath mode using curly braces. In the next example the attributes `row`, `column` and `backgroundcolor` don't allow dynamic settings, but with the curly braces you can jump into XPath evaluation and get the attribute values on the fly:

=== "`layout.xml`"
    ```xml
    <Layout xmlns="urn:speedata.de/2021/xts/en"
     xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">
        <Pageformat height="6cm" width="10cm" />
        <SetVariable variable="x" select="12 * 2"/>
        <SetVariable variable="y" select="36 div 2"/>

        <Record element="data">
            <PlaceObject row="{$x}mm" column="{$y}mm">
                <Box height="1cm" width="3cm" backgroundcolor="{ @col }"/>
            </PlaceObject>
        </Record>
     </Layout>
    ```
=== "`data.xml`"
    ```xml
    <data col="goldenrod"></data>
    ```
=== "Result"
    ![colored box](img/xpath-color.png){: style="height:150px; border: 1px solid black;"}


!!! warning "XML escaping"
    Since the `<` is invalid in XML except at the starting position of a tag name (or another XML node), you need to escape it with `&lt;`. For example a test for “less than” must be written such as `test=" 5 &lt; $value"`. A “greater than” is harmless: `test=" 5 > $value "` is valid XML.

!!! warning "String values in select/test attributes"
    If you want to specify a string as a value in select or test, you need to use single or double quotes such as `<SetVariable variable="foo" select="'a string'">`. Omitting the quotes might fail silently when the contents of the select attribute is interpreted as a child element selection which might be possibly empty.


## Layout functions

* `current-page`
* `current-row`
* `dummytext`
* `even`
* `file-exists`
* `group-height`
* `group-width`
* `last-page-number`
* `number-of-columns`
* `number-of-rows`
* `odd`
* `page-number`
* `roman-numeral`


## XPath functions

* `abs`
* `boolean`
* `ceiling`
* `codepoints-to-string`
* `concat`
* `contains`
* `count`
* `empty`
* `false`
* `floor`
* `last`
* `local-name`
* `lower-case`
* `matches`
* `max`
* `min`
* `not`
* `normalize-space`
* `number`
* `position`
* `replace`
* `reverse`
* `round`
* `string`
* `string-join`
* `string-length`
* `string-to-codepoints`
* `substring`
* `true`
* `tokenize`
* `upper-case`
