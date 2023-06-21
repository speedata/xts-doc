# File organization


This section describes how the necessary files (layout, data, images and font files) must be organized, where they are stored, what they must be called, and so on.

When the Publisher starts, it reads the current (working) directory and all child directories and saves the file names in a list. As soon as a resource is loaded, this list is used to check whether a corresponding file exists. No distinction is made as to which directory the file is located in.

It follows from this:

1. If something changes in the file system during the run, the Publisher will not notice this.
1. It does not matter what the directories are called. The images can, but do not have to be stored in the directory with the name "images".
1. If the working directory is too large, the startup process is slow. A few thousand files in the working directory are usually no problem.

There are exceptions to the rule:

1. You can use `sp --no-local` to instruct the publisher not to search the working directory recursively.
1. With `--extra-dir` you can add a directory to be searched recursively.
1. With `sp --systemfonts`, font files are also searched in directories that are predefined by the system.
1. With `sp --wd DIR` the publisher changes to this directory before starting.

For a description of the parameters see the section on the [command line](commandline.md).

## What names must the data file and the layout file have?

The speedata Publisher looks for the layout with the name layout.xml and the data file with the name data.xml. Both can be adjusted on the command line (`--layout=XYZ` and `--data=XYZ`) and in the configuration file (`layout=XYZ` and `data=XYZ`). See the sections [command line](commandline.md) and [configuration](configuration.md).

<figure markdown>
  ![file structure](img/18-dateisystem.png){ width="100%" }
  <figcaption>Possible file organization in a directory. The name of the subdirectories (folders) is arbitrary.</figcaption>
</figure>



<!--
[[ch-splitlayout]]
## Splitting layout sets of rules into individual files

You can split the layout ruleset into several files. There are two ways to merge the files. On the command line, you can use `--extra-xml` to specify one or more layout rulesets, which are also read in. Alternatively, you can use the mechanism via XInclude, here in the case of a font definition:

~~~xml
<Layout
  xmlns="urn:speedata.de:2009/publisher/en">

  <LoadFontfile name="DejaVuSerif" filename="DejaVuSerif.ttf" />
  ...

</Layout>
~~~

This file can then be included with

~~~xml
<Layout xmlns="urn:speedata.de:2009/publisher/en"
  xmlns:sd="urn:speedata:2009/publisher/functions/en"
  xmlns:xi="http://www.w3.org/2001/XInclude"
  >

  <xi:include href="dejavu.xml"/>
  ...

</Layout>
~~~

The namespace for XInclude must be declared as above, otherwise there will be a syntax error in the XML file.

## Splitting data into individual files

The data file can also be split into several files. XInclude is used for this.

~~~xml
<catalog xmlns:xi="http://www.w3.org/2001/XInclude">
  <xi:include href="globalsettings.xml"/>
  <xi:include href="article0001.xml"/>
  <xi:include href="article0002.xml"/>
  ...
</catalog>
~~~

The namespace for XInclude must be declared in the root node (in the above example, 'catalog').

// EOF -->