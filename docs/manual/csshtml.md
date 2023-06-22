# Using HTML and CSS

HTML markup and CSS styling are a first class citizen in XTS.

See this example:


~~~xml
<Layout xmlns="urn:speedata.de/2021/xts/en"
    xmlns:sd="urn:speedata.de/2021/xtsfunctions/en">

    <LoadFontfile name="CormorantGaramond-Regular" filename="CormorantGaramond-Regular.ttf" />
    <LoadFontfile name="CormorantGaramond-Bold" filename="CormorantGaramond-Bold.ttf" />
    <LoadFontfile name="CormorantGaramond-BoldItalic" filename="CormorantGaramond-BoldItalic.ttf" />
    <LoadFontfile name="CormorantGaramond-Italic" filename="CormorantGaramond-Italic.ttf" />

    <DefineFontfamily name="serif">
        <Regular fontface="CormorantGaramond-Regular" />
        <!-- not strictly necessary in this document: -->
        <Bold fontface="CormorantGaramond-Bold" />
        <Italic fontface="CormorantGaramond-Italic" />
        <BoldItalic fontface="CormorantGaramond-BoldItalic" />
    </DefineFontfamily>

    <Stylesheet>
        p {
            font-family: serif;
        }
        .regular {
            font-feature-settings: "lnum","tnum" ;
        }
        .smcp {
            font-feature-settings: "smcp" ;
        }
    </Stylesheet>

    <Record element="data">
        <PlaceObject>
            <Textblock>
                <Paragraph class="regular">
                    <Value>Text with table figures 1234567890</Value>
                </Paragraph>
                <Paragraph class="smcp">
                    <Value>Text with small caps 1234567890</Value>
                </Paragraph>
            </Textblock>
        </PlaceObject>
    </Record>
</Layout>
~~~

Within `<Value>` use can use HTML formatting:

~~~xml
<PlaceObject>
  <Textblock>
    <Paragraph>
      <Value>A wonderful <b>serenity</b>
          has taken possession
          <i>of my <b>entire soul,</b></i>
          like these sweet mornings.
      </Value>
    </Paragraph>
  </Textblock>
</PlaceObject>
~~~

