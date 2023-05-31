* [TOML format](https://toml.io/en/)

Example:

```toml title="xts.cfg"
# this is a comment
filter="filter.lua"

[variables]
foo = "bar"
bar = 123
```

Defaults:

```toml title="xts.cfg"
data="data.xml"
layout="layout.xml"
jobname="xts"
dummy=false
loglevel="info"
quiet=false
systemfonts=false
verbose=false
trace = []
mode = []
```


Allowed keys:


| Argument    | Type                                            | Description                                                                  |
| ----------- | ----------------------------------------------- | ---------------------------------------------------------------------------- |
| data        | [string](https://toml.io/en/v1.0.0#string)                                          | The name of the data file.                                                   |
| layout      | [string](https://toml.io/en/v1.0.0#string)                                          | The name of the layout file.                                                 |
| dummy       | [boolean](https://toml.io/en/v1.0.0#boolean)                                         | Ignore data file and use `<data />` as the input XML.                        |
| jobname     | [string](https://toml.io/en/v1.0.0#string)                                          | The output name of the PDF, protocol file and other intermediate files.      |
| loglevel    | [string](https://toml.io/en/v1.0.0#string)                                          | Set the log level. One of "debug", "info", "warn", "error".                  |
| quiet       | [boolean](https://toml.io/en/v1.0.0#boolean)                                         | Don't output anything, just log to the protocol file.                        |
| systemfonts | [boolean](https://toml.io/en/v1.0.0#boolean)                                         | Use the fonts from the operating system                                      |
| verbose     | [boolean](https://toml.io/en/v1.0.0#boolean)                                         | Put more debugging information into the protocol file.                       |
| trace       | [string array](https://toml.io/en/v1.0.0#array) | Set one of the trace values. Allowed values are "grid" and "gridallocation". |
| mode        | [string array](https://toml.io/en/v1.0.0#array) | Set the modes during the typesetting run.                                    |
| variables   | [table](https://toml.io/en/v1.0.0#table)        | Set variables.                                                               |