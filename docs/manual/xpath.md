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

The layout functions are in the name space `urn:speedata.de/2021/xtsfunctions/en`.

`sd:aspect-ratio()`
:   Return the result of the division width by height of the given image. (< 1 for portrait images, > 1 for landscape).

    | Argument    | Type    | Optional | Description                                                                                                                                                    |
    | ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | file name   | string  | no       | The name of the file or a URL resource                                                                                                                         |
    | page number | integer | yes      | The page number in the PDF file                                                                                                                                |
    | pdf box     | string  | yes      | One of the PDF boxes: `artbox`, `cropbox`, `bleedbox`, `trimbox` `mediabox`. This defaults to the `cropbox`. Only useful when the first argument is a PDF file |

    The return value is a double.

`sd:attribute()`
:   Return the value of the attribute in the data file.

    | Argument       | Type   | Optional | Description                |
    | -------------- | ------ | -------- | -------------------------- |
    | attribute name | string | no       | The name of the attribute. |

    Assuming that the variable `$attributePrefix` contains the string `"fo"`, the following XPath expressions are equivalent: `@foo`, `@*[local-name() = 'foo']`, `sd:attribute( 'foo' )` and `sd:attribute( ($attributePrefix,'o') )` (notice the argument of the last example is a sequence).


`sd:current-page()`
:   Return the current page number.

`sd:current-row()`
:    Return current row within the the area.

    | Argument | Type   | Optional | Description                                            |
    | -------- | ------ | -------- | ------------------------------------------------------ |
    | area     | string | yes      | The name of the area. It defaults to the default area. |

`sd:decode-base64()`
:   Decode a string with base64 encoding.

    | Argument | Type   | Optional | Description              |
    | -------- | ------ | -------- | ------------------------ |
    | data     | string | no       | The base64 encoded data. |

    The base64 encoded data which has to be stored in a string gets converted into a byte array. Useful for including images stored in the data file. See `sd:file-contents()` and the [base64 example](https://github.com/speedata/xts-examples/tree/main/technical/base64decode).


`sd:decode-html()`
:    Convert a string to HTML.

    | Argument  | Type   | Optional | Description                |
    | --------- | ------ | -------- | -------------------------- |
    | HTML text | string | no       | The escaped HTML contents. |

    Example: `sd:decode-html('&lt;b>bold text&lt;/b>')` creates a HTML structure like putting `<b>bold text</b>` in the data file.


`sd:dummy-text()`
:    Create a lorem ipsum text which is useful for debugging.

`sd:even()`
:    Return true if the given number is even.

    | Argument | Type   | Optional | Description                                  |
    | -------- | ------ | -------- | -------------------------------------------- |
    | number   | number | no       | Return true if the number is an even number. |

`sd:file-contents()`
:   Write the argument to a file in a temporary directory and return the file name.

    | Argument | Type       | Optional | Description                             |
    | -------- | ---------- | -------- | --------------------------------------- |
    | data     | data array | no       | Write the contents to a temporary file. |

    Useful for including images stored in the data file. See `sd:decode-base64()` and the [base64 example](https://github.com/speedata/xts-examples/tree/main/technical/base64decode).

`sd:file-exists()`
:   Return true if the file exists.

    | Argument | Type   | Optional | Description                                                                      |
    | -------- | ------ | -------- | -------------------------------------------------------------------------------- |
    | filename | string | no       | If the filename is not a full path to the file, the known searching rules apply. |

`sd:format-number()`
:    Insert thousands separator into a number.

    | Argument            | Type   | Optional | Description                                        |
    | ------------------- | ------ | -------- | -------------------------------------------------- |
    | number              | double | no       | The number to be formatted.                        |
    | thousands separator | string | no       | The string to be inserted as a thousands separator |
    | decimal comma       | string | no       | The string to be used for the decimal comma        |

    Example: `sd:format-number(-12345678.912, ',', '.')` returns the string `-12,345,678.912`, `sd:format-number(-12345678.912, '.', ',')` the string `-12.345.678,912` (last to arguments swapped).

`sd:group-height()` and `sd:group-width()`
:   Return the height or width of a group.

    | Argument   | Type   | Optional | Description                                                                        |
    | ---------- | ------ | -------- | ---------------------------------------------------------------------------------- |
    | group name | string | no       | The name of the group.                                                             |
    | unit       | string | yes      | Return the height/width of the group in the amount of units instead of grid cells. |

    Example: `sd:group-height('mygroup','cm')` could return `2.74`.


`sd:image-height()` and `sd:image-width()`
:    Return the height or width of an image.

    <div>

    | Argument    | Type    | Optional | Description                                                                                                                                                    |
    | ----------- | ------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | file name   | string  | no       | The name of the file or a URL resource                                                                                                                         |
    | page number | integer | yes      | The page number in the PDF file                                                                                                                                |
    | pdf box     | string  | yes      | One of the PDF boxes: `artbox`, `cropbox`, `bleedbox`, `trimbox` `mediabox`. This defaults to the `cropbox`. Only useful when the first argument is a PDF file |
    | unit        | string  | yes      | Return the height/width of the image in the amount of units instead of grid cells.                                                                             |

    The image dimensions are rather meaningless when the image is a bitmap file (PNG or a JPEG). XTS assumes a PPI (pixels per inch) value of 96. So a 960 pixel wide image has a width of 10 inch or 254 mm. XTS does not extract the PPI values from the image itself.
    </div>


`sd:last-page-number()`
:   Return the last page number of the document. This actually returns the number of pages of the previous run, so it might not be accurate if the number of pages changes in a subsequent run.

`sd:markdown()`
:   Interpret the argument as markdown and return HTML.

    | Argument | Type   | Optional | Description                         |
    | -------- | ------ | -------- | ----------------------------------- |
    | input    | string | no       | The markdown encoded document text. |

    Example: `sd:markdown( '**strong text**' )` returns the string `<strong>strong text</strong>` which gets interpreted as HTML.


`sd:md5()`, `sd:sha1()`, `sd:sha256()`, `sd:sha512()`
:   Calculate hash values.

    | Argument | Type   | Optional | Description                                                   |
    | -------- | ------ | -------- | ------------------------------------------------------------- |
    | source   | string | no       | The text on which the hash function should calculate the sum. |

    Example: `sd:md5( ('Hello, ', 'world') )` returns the string `bc6e6f16b8a077ef5fbc8d59d0b931b9`.

`sd:mode()`
:   Check if mode is set.

    | Argument  | Type   | Optional | Description                                                              |
    | --------- | ------ | -------- | ------------------------------------------------------------------------ |
    | mode name | string | no       | The name of the mode. If it is set, return true, otherwise return false. |

    Example: `sd:mode('print')` returns `true()` if XTS is called with `--mode print` on the command line.



`sd:number-of-columns()`
:   Return the width of an area in grid cells.

    | Argument | Type   | Optional | Description                                            |
    | -------- | ------ | -------- | ------------------------------------------------------ |
    | area     | string | yes      | The name of the area. It defaults to the default area. |


`sd:number-of-rows()`
:   Return the height of an area in grid cells.

    | Argument | Type   | Optional | Description                                            |
    | -------- | ------ | -------- | ------------------------------------------------------ |
    | area     | string | yes      | The name of the area. It defaults to the default area. |

`sd:odd()`
:    Return true if the argument is odd.

    | Argument | Type   | Optional | Description                                 |
    | -------- | ------ | -------- | ------------------------------------------- |
    | number   | number | no       | Return true if the number is an odd number. |

`sd:page-number()`
:    Return the page number of a marker.

    | Argument | Type   | Optional | Description                                                                                                                 |
    | -------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------- |
    | name     | string | no       | Return page number of a marker. The marker has to be defined with the command [`<Mark>`](../reference/cmdreference/mark.md) |

`sd:roman-numeral()`
:    Return a number as a roman numeral.

    | Argument | Type   | Optional | Description                  |
    | -------- | ------ | -------- | ---------------------------- |
    | number   | number | no       | a number as a roman numeral. |

    Example: `sd:roman-numeral(13)` returns the string `XIII`.

`sd:to-unit()`
:    Convert units to other units.

    | Argument  | Type   | Optional | Description                                  |
    | --------- | ------ | -------- | -------------------------------------------- |
    | length    | string | no       | The length that should be converted          |
    | unit      | string | no       | The resulting unit                           |
    | precision | number | yes      | The number of digits after the decimal point |

`sd:total-pages()`
:    Return the number of pages in a graphics file.

    | Argument  | Type   | Optional | Description           |
    | --------- | ------ | -------- | --------------------- |
    | file name | string | no       | The name of the file. |

    This function returns the number of pages in a PDF file. If the image is not a PDF file, the function returns 1.

`sd:variable()`
:   Return the value of a variable. The variable name can be created dynamically.

    | Argument      | Type   | Optional | Description               |
    | ------------- | ------ | -------- | ------------------------- |
    | variable name | string | no       | The name of the variable. |

    Assuming that the variable `$variablePrefix` contains the string `"fo"`, the following XPath expressions are equivalent: `$foo`, `sd:variable( 'foo' )` and `sd:variable( ($variablePrefix,'o') )` (notice the argument of the last example is a sequence).


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
