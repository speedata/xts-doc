# Installation


1. Download ready to run package (the recommended way):

    Go to [the download page](https://github.com/speedata/xts/releases/latest) and get the package for your operating system. You can unzip the file anywhere in the filesystem you want. You don’t need root/administrator rights to use XTS this way. You need to set the PATH variable to the bin directory of the unzipped archive.



2. Build from source

    Download the [ZIP file from the releases page](https://github.com/speedata/xts/releases/latest) or [clone the git repository](https://github.com/speedata/xts.git) with

    `git clone https://github.com/speedata/xts.git`

    and build the xts with

    ```
    cd xts
    rake build
    ```

    The xts command is now in the `bin/` directory.

    Requirements for building from source:

    * Go version 1.21 (or later)
    * Ruby and rake. These are not strictly necessary, if you want to avoid rake, check out the `Rakefile` and run the go build command listed in the `task :build do` section.


