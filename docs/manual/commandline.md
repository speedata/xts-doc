---
title: Command line
---

# Running XTS on the command line

```
$ xts <Command> <Parameter> <Parameter> ...
```

## Description of the commands

`run`
:   Load layout and data files and create PDF (default)

`clean`
:   Remove auxiliary and protocol files

`doc`
:   Open the documentation in a web browser (Linux, Windows, macOS)

`list-fonts`
:    List available fonts

`new`
:    Create simple layout and data file to start. Provide optional directory

`version`
:    Print version number and exit

## Command line parameters


`-c, --config=NAME`
:   Read the config file with the given NAME. Default: 'xts.cfg'

`--data=NAME`
:   Name of the data file. Defaults to 'data.xml'

`--dummy`
:   Don't read a data file, use '`<data />`' as input

`--dumpoutput=FILENAME`
:   Complete XML dump of generated PDF file

`--extradir=DIR`
:   Additional directory for file search

`--filter=NAME`
:   Run [Lua process](luafilter.md) before the publishing run

`--jobname=NAME`
:   The name of the resulting PDF file (without extension), default is 'xts'

`--layout=NAME`
:   Name of the layout file. Defaults to 'layout.xml'

`--loglevel=LVL`
:   Set the log level for the console to one of debug, info, warn, error

`--runs=N`
:   Run XTS N times

`--quiet`
:   Run XTS in quiet mode (no output to STDOUT)

`--suppressinfo`
:   Create a reproducible document

`--systemfonts`
:   Use system fonts

`--trace=NAMES`
:   Set the trace to one or more of grid, allocation

`--verbose`
:   Put the logging output also to the terminal window (STDOUT)



