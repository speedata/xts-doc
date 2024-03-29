# Lua-Filter / pre-processing

Sometimes you may want to convert the data into another format or check for correctness before the actual PDF creation.
For this purpose there is the possibility to execute a Lua script before the actual publishing run.
Lua is a simple but powerful programming language that is intended to be built into other programs as a scripting language.

Some use cases found in examples repository.

## Calling the Lua script

The filter is started either via the command line

~~~lua
xts --filter myfile.lua
~~~

or via the configuration file, which must contain the following entry

~~~
filter=myfile.lua
~~~

The specified Lua script will be executed before the PDF file generation starts.
It must be within the XTS search path.
Therefore the main application of this pre-processing is the transformation of data into a format suitable for XTS.
This way CSV or Excel files can be converted to XML and then the PDF generation can be started.
It is also possible to validate data.

The application options are described below, and at the very end there is another overview of the built-in functions and methods.

## Validate input data

There are several ways to validate RELAX NG files. Beside a variant to validate the schema directly in the XML editor (see the corresponding section in the manual) there is the possibility to use an external program for this. One of these is Jing. It is delivered with the Publisher.

In the Lua preprocessing there is a function that does the validation:

~~~lua
runtime = require("runtime")
runtime.validate_relaxng(‹xmlfile›, ‹schemafile›)
~~~

The function returns false and the error message in case of an error. Example:

~~~lua
-- adjust the paths, of course
runtime = require("runtime")
ok, msg = runtime.validate_relaxng("layout.xml","../schema/layoutschema-en.rng")
if not ok then
    print(msg)
    os.exit(-1)
end
~~~

This is saved in a file, e.g. `valididate.lua` and then the publisher is called with

~~~
sp --filter validate.lua
~~~

Before each run, the system checks whether the layout file corresponds to the schema and only then does processing continue.

!!! note "XML validation"

    You can check not only the layout file for correctness, but also all other XML files.
    But for this you have to create your own RELAX NG schema.
    Instructions are available at https://speedata.github.io/relaxngtutorial-de/.
    Depending on the data file this is also quite easy.
    Especially if you get data from external sources again and again, you can be sure that the desired structure is kept.

## Executing a transformation

An XSLT transformation processes an XML file with an XSLT script and generates an output file.
XSLT is a programming language designed for processing XML data.
Often data from Product Information Management (PIM) systems or databases is not in the form that is optimal for the publisher. With XSLT you can process and modify such output data.

The program saxon (supplied with XTS, Java runtime needed) can execute an XSLT script. The call is the following:

~~~lua
runtime = require("runtime")
runtime.run_saxon(‹table with parameters›)
~~~

For example:

~~~lua
runtime = require("runtime")
ok, msg = runtime.run_saxon({ key = value, key = value, ... }

-- quit the publishing process if the transformation fails
if not ok then
    print(msg)
    os.exit(-1)
end
~~~

Allowed key/value pairs are:

| Key             | Value                             |
| --------------- | --------------------------------- |
| source          | Source file (XML)                 |
| stylesheet      | Stylesheet file (XSL)             |
| out             | Result                            |
| initialtemplate | Name of the template to be called |
| params          | Table with the key/value pairs    |


Example:

~~~lua
runtime = require("runtime")
ok, msg = runtime.run_saxon({stylesheet = 'json2xml.xsl',
                             out = 'data.xml',
                             initialtemplate = 'main',
                             params = { ["key"] = value }})
~~~

See also the example in examples repository.

## Creating XML files

You can also create the data file to be processed with the Lua script. For this purpose there is the function encode_table() in the module xml, which creates an XML file from a Lua table.

The script

~~~lua
xml = require("xml")
tbl = {
    ["_type"] = "element",
    ["_name"] = "data",
    {
       ["_type"] = "element",
       ["_name"] = "child",
       "Hello, world",
    }
}


ok, msg = xml.encode_table(tbl)
if not ok then
    print(msg)
    os.exit(-1)
end
~~~

generates the XML file

~~~xml
<data><child>Hello, world</child></data>
~~~

which is available for the next publisher run. This is particularly useful if the data source is not in XML.

## Processing of Excel files

A common use case is that the data is to be read from Excel files for processing. For this purpose, the module xlsx contains the function open() which opens an existing file:

~~~lua
xlsx = require("xlsx")
spreadsheet, err = xlsx.open("myfile.xlsx")
if not spreadsheet then
    print(err)
    os.exit(-1)
end
~~~

The object spreadsheet contains the individual worksheets.
The number of worksheets can be determined using the length operator and the individual worksheets can be determined using the index (1 is the first worksheet).

~~~lua
numWorksheets = #spreadsheet
ws = spreadsheet[1]
~~~

The object ws can be used to access the cell contents directly. To do this, it is called as a function and returns a character string. The first cell in the upper left corner has the coordinates 1,1, the first cell in the second row 1,2 and so on.

~~~lua
cell1 = ws(1,1)
cell2 = ws(1,2)
~~~

The name of the worksheet can be determined by the value name:

~~~lua
name = ws.name
~~~
## Read CSV files

Similar to Excel files, CSV files can also be read in directly. However, the structure is simpler because there is only one “worksheet”.

~~~lua
csv = require("csv")
csvtab, msg = csv.decode("myfile.csv",{columns = {1,2,3}})
if not csvtab then
    print(msg)
    os.exit(-1)
end
~~~

The second parameter at csv.decode() is optional. In this example only columns 1, 2 and 3 are output. The result is a table of rows. Each row is in turn a table containing the individual values of the row.

The example repository shows how to create an XML file from the CSV file.

## Function reference

### Runtime

In this module all functions and settings are collected, which are of a more general nature.

`projectdir`
:   A string containing the current project directory (the directory with the layout.xml or publisher.cfg file)

`variables`
:   A table with all variables specified by -v on the command line or in the configuration file with vars=…​.

`finalizer`
:   If a function is assigned to this variable, it will be called after PDF creation (callback). The function has no parameters and no return value.

    ~~~lua
    runtime = require("runtime")

    function finished()
        print("PDF is finished now.")
    end

    runtime.finalizer = finished
    ~~~

`options`
:   Table with configuration values (see how to configure XTS). Can be used for reading and writing the settings.

`validate_relaxng(‹xml file›, ‹schema file›)`
:   This function validates the specified XML file with the RELAX NG (XML syntax) schema specified in the second parameter. The return is a boolean value that is true if the command was executed without errors. Otherwise a second return value (string) is returned, which contains the error message.

`run_saxon(‹table›)`
:   This function calls the saxon program supplied with XTS. It expects the arguments as a table with the keys explained in the table below. The value of params is a table of key value pairs for parameters that are passed to saxon. The return is a boolean value which is true if the command was executed without errors. Otherwise a second return value (string) is returned, which contains the error message.

    | Key             | Value                             |
    | --------------- | --------------------------------- |
    | source          | Source file (XML)                 |
    | stylesheet      | Stylesheet file (XSL)             |
    | out             | Result                            |
    | initialtemplate | Name of the template to be called |
    | params          | Table with the key/value pairs    |


`execute(‹table with arguments›)`
:   Runs a program and prints its output to the console. For example, to start XTS itself, the following syntax works:

`runtime.execute({"sp","--runs","2"})`
:   If necessary, the first parameter (the program name) must be specified with absolute path of the program. Under Windows, forward slashes (/) also work as separators instead of backward slashes (\).

`find_file(‹filename or URL›)`
:   Find the resource and return a full path on the local disk to access the resource. Returns nil or false and perhaps an error message if it can’t find the resource.

### xml

The XML module is used to create or read XML files.

`xml.encode_table(‹table›,[filename])`
:   Creates an XML file (data.xml or the optionally given filename) of the passed table. Return value 1 is a bool (success), value 2 is the error message if the first value is false. The table has the following structure:

    ~~~lua
    element = {
        ["_type"] = "element",
        ["_name"] = "element name"
        attribute1 = "value1",
        attribute2 = "value2",
        child1,
        child2,
        child3,
        ...
    }
    ~~~

    child1, …​ are either strings, elements or comments. Comments have the following form:

    ~~~lua
    comment = {
             _type = "comment",
             _value = " This is a comment! "
       }
    ~~~

`decode_xml(filename›)`
:   Reads an XML file and creates a table in the format from encode_table. Return value 1 is a bool (success), value 2 is the error message if the first value is false or the table if the first value is true.

### CSV

CSV files

`decode(‹filename›, ‹parameter›)`
:   Reads a CSV file. The return value is a table or, in case of an error, false and an error message.

    The parameters are encoded in a table:

    | Parameter | Description                                                                                                                                          |
    | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
    | charset   | If the CSV file is Latin-1 encoded, this value must be ISO-8859-1. Other encodings on request. The default (without the charset parameter) is UTF-8. |
    | separator | Either a comma (default), a semicolon or the appropriate separator.                                                                                  |
    | columns   | A table containing the desired columns in their order. For example, {3,2,1} for the first three columns in reverse order.                            |


### xlsx

Reads an Excel file.

`open(‹filename›)`
:   Opens the specified file. The return value is a spreadsheet object or, in case of an error, false and an error message.

    The spreadsheet object contains the individual worksheets. The number of worksheets can be determined with the `#` operator. The individual worksheets can be accessed with the index operator `[]`, where the first worksheet has index 1.

    The individual worksheets can be used as functions with two parameters ([see example above](#processing-of-excel-files)). The parameters are the x and y coordinates of the cell to be read, the first cell in the upper left corner has the coordinate 1,1. The dimensions of the content can be determined using the parameters `minrow`, `maxrow`, `mincol` and and `maxxcol`. The name is contained in the parameter `name`.

`string_to_date(‹string›)`
:   Converts a number (encoded as a string) into a date. Returned is a table with the keys day, month, year, hour, minute and second. Example: xlsx.string_to_date("43458") results in

    ~~~lua
    {
      ["day"] = "24"
      ["month"] = "12"
      ["year"] = "2018"
      ["hour"] = "0"
      ["minute"] = "0"
      ["second"] = "0"
    }
    ~~~

### http

The HTTP library is described at <https://github.com/cjoudrey/gluahttp>.