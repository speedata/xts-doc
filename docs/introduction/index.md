# About XTS


XTS is a non-interactive tool for creating PDF from XML data. It uses layout instructions (in a programming language) together with CSS styles to create PDF output:

![XML to PDF schema](img/schema.svg)


The idea is to have a strict separation of data and layout.

## What is it all for?

Many different documents can be created with XTS. Classical use cases are

* Product catalogues
* Travel guides
* Price lists
* Data sheets

and many other documents, where it is important to obtain a result that is reproducible, fast and reliable and also “beautiful”.

## Beautiful and fully automatic

XTS is a non-interactive publishing software. This means there is no graphical user interface (GUI).
All instructions must be established before the publishing process and determine how the data is arranged in the PDF.
The unique combination of sophisticated algorithms and programmability allows extremely flexible layouts to be created that were previously reserved for interactive desktop publishing (DTP) programs such as Adobe’s InDesign.

## Where can I get the software and how is it run?

The software can be downloaded for free ([see chapter Installation](../reference/installation.md)) and is started via the console or shell.
The command to start XTS is called `xts`.
Therewith, all functionality can be used.
Parameters can be specified via the [command line](../manual/commandline.md) or a [configuration file](../manual/configuration.md).

```
$ xts
```

See the [command line section](../manual/commandline.md) for explanations on how to start XTS.

## Examples

There is a separate repository with examples on  [Github](https://github.com/speedata/xts-examples). There you can find complete documents, which you can use to try out different functionality.




