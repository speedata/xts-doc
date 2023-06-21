# LoadFontfile



Load a font file (.otf, .ttf, .pfb) and associate it with an internal name. If a glyph is not found in the font file, an error will be raised (this can be configured via the Options command). You can specify fallbacks as a child element of Loadfontfile.



##  Child elements

(none)

##  Parent elements

[Layout](../layout.md)


## Attributes



`filename` (text)
:   The name (with extension) of the font file.




`marginprotrusion` (0 up to 100, optional)
:   The amount of protrusion glyphs like -, . and - stick into the right margin. Highly font dependent. Defaults to 0.




`name` (text)
:   The internal name of the font file. To be used within [DefineFontfamily](../definefontfamily.md).




## Example






## Info

The fonts are optionally taken from the local search path. On Windows the path `%WINDIR%\Fonts` (usually `C:\Windows\Fonts`) and on Mac OS X the paths `/Library/Fonts` and `/System/Library/Fonts` can be used as fallbacks for fonts. This can be configured with the setting `fontpath`.




