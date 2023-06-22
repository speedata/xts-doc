# Barcode



Print a 1d or 2d barcode. To be used in [PlaceObject](../placeobject.md).



##  Child elements

(none)

##  Parent elements

[PlaceObject](../placeobject.md)


## Attributes



`color` (optional)
:   Color of the barcode. Must be defined with [DefineColor](../definecolor.md) before use. Currently only used for QR codes.




`eclevel` (optional)
:   Set the error correction level for QR-codes. If not provided, the system uses the maximum level for minimum size. The higher the level, the more error correction is in the QR-code.



    `L`
    :    Set the lowest level (1) with approx. 7% recovery.



    `M`
    :    Set the second lowest level (2) with approx. 15% recovery.



    `Q`
    :    Set the second highest level (3) with approx. 25% recovery.



    `H`
    :    Set the highest level (4) with approx. 35% recovery.




`fontfamily` (text, optional)
:   Name of the font of the text that can be placed beneath the barcode. Not used in all codes.




`fontsize` (text, optional)
:   Set the font size. You can use a name predefined with [DefineFontsize](../definefontsize.md) or a string such as "10pt/12pt" to set the font size and the leading. Defaults to 'text'.




`height` (number or length, optional)
:   Height of the barcode.




`keepfontsize` (yes or no, optional)
:   Try to keep the size of the requested font. Works with EAN13 only.




`overshoot` (number, optional)
:   The factor denoting the extra length of the outer and middle bar. Only useful with EAN13.




`select` ([XPath expressions](../../../manual/xpath.md))
:   The data to be encoded in the barcode.




`showtext` (optional)
:   Should the text be written under the barcode?



    `yes`
    :    Write text beneath the barcode.



    `no`
    :    Don't display text.




`type` ()
:   Type of the barcode. One of `EAN13`, `Code128` or `QRCode`.



    `QRCode`
    :    Create an “optimal” QR code in terms of error correction and size.



    `Code128`
    :    Generate a code 128 barcode for numbers and text.



    `EAN13`
    :    Create an EAN13 barcode for 13 digits.




`width` (number or length, optional)
:   Width of the barcode




## Example

```xml
<PlaceObject>
  <Barcode select="'speedata Publisher'" type="Code128" showtext="yes"/>
</PlaceObject>
```

gives



image::ref-code128-speedata-publisher.png[width=auto]
```xml
<PlaceObject>
  <Barcode select="4242002518169" type="EAN13"/>
</PlaceObject>
```

becomes



image::ref-ean13-supertex.png[width=300]

And finally the QR code


```xml
<PlaceObject>
  <Barcode select="'http://www.speedata.de'" type="QRCode" height="5"/>
</PlaceObject>

```

looks like



image::ref-speedata-publisher-qrcode.png[width=300]





