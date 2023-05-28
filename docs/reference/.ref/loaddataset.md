# LoadDataset



Load an XML file previously written by [SaveDataset](../savedataset.md) (attribute name) or a well formed XML file (attribute href). The regular data processing is interrupted and the contents of the data file is taken as a data source. If the file does not exist, the call to [LoadDataset](../loaddataset.md) is ignored.



##  Child elements

(none)

##  Parent elements

[AtPageCreation](../atpagecreation.md), [AtPageShipout](../atpageshipout.md), [Case](../case.md), [Contents](../contents.md), [ForAll](../forall.md), [Function](../function.md), [Loop](../loop.md), [Otherwise](../otherwise.md), [Record](../record.md), [Until](../until.md), [While](../while.md)


## Attributes



`href` (text, optional)
:   Filename of the XML file to load. Example: `myfile.xml`.




`name` (text, optional)
:   Name of the data file. Example: toc




## Example

```xml
<Record element="articles">
  <LoadDataset name="toc"/>
  <ClearPage/>
  <ProcessNode select="article"/>
</Record>

```





