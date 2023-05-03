# Tr



Tablerow



##  Child elements

[ForAll](../forall.md), [Loop](../loop.md), [Message](../message.md), [Switch](../switch.md), [Td](../td.md), [Value](../value.md)

##  Parent elements

[Table](../table.md)


## Attributes



`align` (optional)
:   Horizontal alignment of the table cells in this row.



    `left`
    :    The contents is left aligned (ragged right). This is the default.



    `right`
    :    The contents of the cell is right aligned.



    `center`
    :    The contents of the cell is aligned at the center, with ragged right and left margin.



    `justify`
    :    Justified text with straight margins.




`backgroundcolor` (text, optional)
:   Background color of each cell in this row.




`break-below` (optional)
:   Allow a table break between this row and the following.



    `yes`
    :    Allow a table break between this row and the following (default).



    `no`
    :    Disable a table break between this row and the following.




`data` ([XPath expressions](../../manual/xpath.md), optional)
:   Data that can be accessed via `$_last_tr_data` in the tablefoot and tablehead.




`minheight` (number or length, optional)
:   Minimum row height in grid cells or length.




`sethead` (optional)
:   Use this line for future table heads.



    `yes`
    :    Use this line for future table heads.



    `no`
    :    No special treatment of this line (default).



    `clear`
    :    Delete head. Next pages will have no head until new one is set with 'yes'.




`top-distance` (number or length, optional)
:   The space above this row if it is not the first line on a new page / area.




`valign` (optional)
:   Vertical alignment of the table cells in this row.



    `top`
    :    The objects in this row are aligned at the top.



    `middle`
    :    The objects in this row are aligned at the middle axis.



    `bottom`
    :    The objects in this row are aligned at the bottom.




## Example

```xml
<Tr minheight="8mm" backgroundcolor="yellow">
  <Td align="center"><Paragraph><Value>A</Value></Paragraph></Td>
  <Td><Paragraph><Value>B</Value></Paragraph></Td>
  <Td align="center"><Paragraph><Value>C</Value></Paragraph></Td>
  <Td align="center"><Paragraph><Value>D</Value></Paragraph></Td>
  <Td><Paragraph><Value>E</Value></Paragraph></Td>
</Tr>
```





