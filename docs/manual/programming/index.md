# Programming

Certainly the most important feature of XTS is the ability to implement very flexible layout requirements. This is mainly achieved by the built-in programming language in connection with the query options of XTS.

!!! note "execution time"
    The program execution runs simultaneously with the creation of the PDF. Therefore, XTS can react very flexibly to the input data. Queries such as “Is there still enough space for this object?” are thus possible. This distinguishes XTS from other software for creating PDF files. Basic programming knowledge is required to use the full functionality of XTS. The programming language has been kept as simple as possible to maintain the readability of the layout.

## Two programming levels

There are two programming levels. The more global one is on the layout XML level and uses constructs such as `<SetVariable>` or `<Loop>`. This is called the XTS layout language or the host language. There is another level called XPath, which is more locally focused and used within attributes from the host language. For example the the switch/case command has an attribute called `test` which expects an XPath language expression that evaluates to `true()` or to `false()`. In contrast to the host language, XPath is a well-known language that is used, for example, in XSLT.

This chapter describes the XTS layout language. For an introduction to XPath see for example the one at [W3Schools](https://www.w3schools.com/xml/xpath_intro.asp).

## Variables

All variables are globally visible. This means that a variable never becomes invalid (except in [functions](functions.md)). Here’s an example:

=== "`layout.xml`"
    ~~~xml
    <Layout xmlns="urn:speedata.de/2021/xts/en"
        xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

        <Record element="data">
            <ProcessNode select="article" />
            <!--
                At this point all child elements from “article”
                have been visited by executing the previous
                command (<ProcessNode>).
                The variable 'no' gets set
                to 1,2 and 3 respectively in each call of the
                corresponding <Record element="article"> command.

                When the next command (<Message>) is executed,
                all child elements 'article' are visited.
                The global variable 'no' is now set to 3:
            -->
            <Message select="$no" />
        </Record>

        <Record element="article">
            <SetVariable variable="no" select="@number" />
        </Record>

    </Layout>
    ~~~
=== "`data.xml`"
    ~~~xml
    <data>
      <article number="1" />
      <article number="2" />
      <article number="3" />
    </data>
    ~~~


The output of the command [`<Message>`](../../reference/cmdreference/message.md) is 3. If the variable `no` was declared with local visibility, it could not be read in the data element.

The global visibility is necessary because the program execution in the layout sometimes “jumps back and forth”. At the end of the page the content of [`<AtPageShipout>`](../../reference/cmdreference/atpageshipout.md) is executed in the current page type. It must also be possible to access the variables there.

In variables not only simple values can be stored, but also complex XML sections:

~~~xml
<Record element="data">
    <SetVariable variable="foo">
        <Paragraph>
            <Value>Hello, world!</Value>
        </Paragraph>
    </SetVariable>
    <PlaceObject>
        <Textblock>
            <Value select="$foo" />
        </Textblock>
    </PlaceObject>
</Record>
~~~
Results in the expected issue of "Hello, world!". A use case is to store table width declarations:

~~~xml
<SetVariable variable="tablecolumns">
  <Columns>
    <Column width="1cm"/>
    <Column width="4mm"/>
    <Column width="1cm"/>
  </Columns>
</SetVariable>
~~~

and then use them in several tables:

~~~xml
<PlaceObject>
  <Table>
    <Value select="$tablecolumns"/>
    <Tr>
      ..
    </Tr>
  </Table>
</PlaceObject>
~~~

The one-time definition and reuse saves typing work and reduces the sources of error.

## Execution time

The contents of variables containing child elements are evaluated immediately. I.e. in the following case

~~~xml
<SetVariable variable="greeting">
    <Value>nice</Value>
</SetVariable>

<SetVariable variable="tmp">
    <Value select="$greeting"/>
</SetVariable>

<SetVariable variable="greeting">
    <Value>cruel</Value>
</SetVariable>

<PlaceObject>
    <Textblock>
        <Paragraph>
            <Value>Hello, </Value>
            <Value select="$tmp"/>
            <Value> world!</Value>
        </Paragraph>
    </Textblock>
</PlaceObject>
~~~

the variable greeting must already be defined. Subsequent modification of the output in the paragraph does not happen. The result is “Hello, nice world!”.

It follows that the variables must not contain any output commands, such as `<PlaceObject>` or `<ClearPage>`, since these would take effect immediately.

## Adding contents to a variable

It is simple to add contents to existing variables by using the `<Value>` Command. The idea is to use the current contents of the variable by using `<Value select="$myvar" />`:

~~~
variable =
   previous contents of $variable
   more contents
~~~

See the following example:

~~~xml
<SetVariable variable="foo">
    <Value>Hello, nice</Value>
</SetVariable>

<SetVariable variable="foo">
    <Value select="$foo"/>
    <Value> world!</Value>
</SetVariable>

<!-- prints “Hello, nice world!” -->
<PlaceObject>
    <Textblock>
        <Paragraph>
            <Value select="$foo" />
        </Paragraph>
    </Textblock>
</PlaceObject>
~~~

This also works for more complex XML structures:

~~~xml
<SetVariable variable="chapter">
  <Value select="$chapter"/>
  <Element name="entry">
    <Attribute name="chaptername" select="@name"/>
    <Attribute name="page" select="sd:current-page()"/>
  </Element>
</SetVariable>
~~~

<!-- An example of copy of in practice is the assembly of XML structures with which information can be stored. This example is described in detail in the Cookbook, there in the section Create directories (XML structure). -->


## Case distinctions

Case distinctions correspond to the construction switch/case from C-like programming languages.
They are applied in XTS as follows:

~~~xml
<Switch>
  <Case test="$i = 1">
    ...
  </Case>
  <Case test="$i = 2">
    ...
  </Case>
   ...
  <Otherwise>
    ...
  </Otherwise>
</Switch>
~~~

All commands within the first possible `<Case>` case are processed if the condition in test applies there. In `test`, an XPath expression is expected that returns `true()` or `false()`, like `$i = 1`, and if no case succeeds, the contents of the optional `<Otherwise>` section will be executed.

## Loops

There are various loops in XTS. The simple variant is `<Loop>`:

~~~xml
<Loop select="10">
  ...
</Loop>
~~~

This loop is run through 10 times.

This command executes the enclosed commands as many times as the expression in select results in. The loop counter is stored in the variable `_loopcounter`, unless otherwise set by `variable="..."`.

Besides the simple loop there are also loops with conditions:

~~~xml
<Record element="data">
  <SetVariable variable="i" select="1"/>
  <While test="$i &lt;= 4">
    <PlaceObject>
      <Textblock>
        <Paragraph>
          <Value select="$i"/>
        </Paragraph>
      </Textblock>
    </PlaceObject>
    <SetVariable variable="i" select="$i + 1"/>
  </While>
</Record>
~~~

The while loop executes the enclosed commands as long as the condition is "true". The numbers 1 to 4 are output.

The expression `$i &lt;= 4` must be read as `$i <= 4`, because the opening angle bracket at this point in the XML is a syntax error. The loop above is executed as often as the content of the variable `i` is less than or equal to 4. Don’t forget to increase the variable as well, otherwise an infinite loop is created.

In addition to the while loop, there is also the until loop, which works in the same way:

~~~xml
<Record element="data">
    <SetVariable variable="i" select="1" />
    <Until test="$i &lt;= 4">
        <PlaceObject>
            <Textblock>
                <Paragraph>
                    <Value select="$i" />
                </Paragraph>
            </Textblock>
        </PlaceObject>
        <SetVariable variable="i" select="$i + 1" />
    </Until>
</Record>
~~~

Since the until loop is executed until the condition is true, only the number 1 is output.

## Data Structures

XTS does not offer direct support for data structures such as arrays (fields) or dictionaries (hashes or dictionaries). These can be simulated using variables. The field a1, a2, …​, ai could be filled as follows:

~~~xml
<SetVariable variable="{ concat('a',1) }" select="'Value for a1'"/>
<SetVariable variable="{ concat('a',2) }" select="'Value for a2'"/>
...
~~~

Of course, a1 could also be specified directly as the variable name. In this example, both the prefix and the suffix could be created dynamically:

~~~xml
<SetVariable variable="prefix" select="'a'" />
<SetVariable variable="{ concat($prefix,1) }" select="'Value for a1'"/>
<SetVariable variable="{ concat($prefix,2) }" select="'Value for a2'"/>
...
~~~

The read access goes via `sd:variable(…​)`:

~~~xml

<SetVariable variable="prefix" select="'a'" />
<Message select="sd:variable( ($prefix,1) )"/>
<Message select="sd:variable( ($prefix,2) )"/>
...
~~~

The function `sd:variable()` concatenates the text value of all entries of the first argument as a string and takes the result as variable name.

